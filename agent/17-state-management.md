# 17 — Agent State Management

## Goal

The KB is stateless. The agent (or its platform) **must maintain state** across weeks. This file defines the minimum data structure an agent should store and update during a 12 Week Year coaching relationship.

---

## Why State Matters

The 12 Week Year requires memory across sessions:
- The 3-year vision does not change week to week.
- Execution scores must accumulate over 12 weeks.
- Obstacles diagnosed in week 3 may reappear in week 7.
- The agent must know which emotional zone the user is in.

Without persistent state, the agent treats every conversation as the first one. The coaching collapses.

---

## Minimum Agent State JSON

```json
{
  "user_id": "unique_identifier",
  "current_cycle": {
    "cycle_number": 1,
    "start_date": "2026-01-06",
    "end_date": "2026-03-31",
    "break_week_start": "2026-04-06",
    "status": "active"
  },
  "vision": {
    "long_term": "...",
    "three_year": "...",
    "updated_at": "2026-01-06"
  },
  "goals": [
    {
      "id": "g1",
      "title": "Launch lead magnet",
      "description": "Create and publish a PDF lead magnet + landing page",
      "tactics": [
        {
          "id": "t1",
          "description": "Write 1 LinkedIn post",
          "type": "recurring",
          "frequency": "3x/week",
          "estimated_minutes": 30,
          "calendar_blocks": [
            {"day": "Mon", "start": "08:00", "end": "08:30"},
            {"day": "Wed", "start": "08:00", "end": "08:30"},
            {"day": "Fri", "start": "08:00", "end": "08:30"}
          ]
        }
      ]
    }
  ],
  "weekly_scores": [
    {
      "week": 1,
      "planned": 12,
      "done": 12,
      "score": 100,
      "notes": "Strong start"
    },
    {
      "week": 2,
      "planned": 12,
      "done": 10,
      "score": 83,
      "notes": "Missed 2 due to travel"
    }
  ],
  "check_in": {
    "day_of_week": "Monday",
    "time": "09:00",
    "next_scheduled": "2026-01-20T09:00:00"
  },
  "agent_notes": {
    "emotional_zone": "grind",
    "last_obstacle": "Travel disrupted schedule",
    "recommended_adjustment": "Shift Tuesday tactic to Sunday evening when travel is expected",
    "break_week_planned": false
  }
}
```

---

## State Update Rules

### At Cycle Start
- Write vision, goals, tactics, calendar blocks.
- Set `current_cycle.status = "active"`.
- Initialize `weekly_scores = []`.
- Set `check_in.next_scheduled` to first Monday after cycle start.

### After Every Weekly Check-In
1. Ask user: "How many tactics did you complete this week?"
2. Append new score object to `weekly_scores`.
3. Update `agent_notes.emotional_zone` based on week number (see `16-emotional-cycle.md`).
4. If score < 65%, write `agent_notes.last_obstacle` and `recommended_adjustment`.
5. Update `check_in.next_scheduled` to next week same time.

### When User Reports Obstacle
- Log the obstacle in `agent_notes.last_obstacle`.
- Generate `recommended_adjustment` using `11-troubleshooting.md`.
- Store both. Do not discard.

### During The Swamp (Weeks 5–7)
- Set `agent_notes.emotional_zone = "swamp"`.
- Pull user state into context along with `03-vision.md`.
- Proactively message if the user misses check-in: "This is the week most people quit. We don't."

### At Break Week
- Set `current_cycle.status = "break"`.
- Calculate cycle average score.
- Prompt user: rest, reflect, preview next cycle.
- Set `agent_notes.break_week_planned = true`.

### At New Cycle Start
- Increment `current_cycle.cycle_number`.
- Update dates.
- Archive previous goals or transfer ongoing ones.
- Clear `weekly_scores`.
- Reset `agent_notes.emotional_zone = "launch"`.

---

## Agent Context Assembly at Runtime

Before every interaction, the agent should assemble context in this order:

1. **System prompt** (from `agent-prompts.md`)
2. **KB rules** (from `00-agent-index.md`)
3. **User state** (the JSON above, serialized)
4. **Relevant KB sections** based on situation:
   - New user → `10-first-conversation.md`
   - Weekly check-in → `08-execution-protocol.md`
   - Score < 65% → `08-execution-protocol.md` + `11-troubleshooting.md`
   - Week 5–7 → `16-emotional-cycle.md` + user vision
5. **Examples** if user is stuck → relevant `examples/`

---

## Memory Pitfalls

| Pitfall | Fix |
|---------|-----|
| Forgetting the user's vision | Inject vision into context every week after week 3 |
| Losing track of execution scores | Maintain `weekly_scores` array; never let the user self-report without updating state |
| Not knowing which week it is | Derive from `current_cycle.start_date` and today's date |
| Ignoring past obstacles | Search `agent_notes` history before diagnosing a new obstacle |
| Letting the user re-describe goals mid-cycle | Lock goals. If user proposes new goal, reference stored goals and refuse |

---

## State Migration Between Cycles

When moving from cycle N to cycle N+1:

1. **Ongoing tactics** (formed into identity) get "archived" status but stay in state as active habits.
2. **Vision** is read-only unless the user explicitly asks to rewrite it.
3. **New goals** replace old goals. Tactics are regenerated.
4. **Previous `weekly_scores`** are archived to `past_cycles` array.
5. **Emotional zone** resets to `launch`.

```json
{
  "past_cycles": [
    {
      "cycle_number": 1,
      "average_score": 87,
      "goals_completed": ["g1"],
      "weekly_scores": [ ... ]
    }
  ]
}
```

This creates a longitudinal record of the user's performance and evolution.

---

## Minimal Viable State

If storage is limited, keep only:
1. `vision.three_year` (string)
2. `goals` (array of current tactics + calendar blocks)
3. `weekly_scores` (array of {week, score})
4. `current_cycle.week_number` (int)
5. `agent_notes.last_obstacle` (string)

Everything else can be reconstructed from these five fields.

