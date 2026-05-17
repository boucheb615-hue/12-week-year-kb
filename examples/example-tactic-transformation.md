# Example E: Tactic Transformation (Weak → Strong Plan)

## Context

A user wants to "get better at public speaking" in 12 weeks. This example shows how an agent would diagnose the weak plan and transform it into a strong, executable plan using the Tactic Design Rules from `12-tactic-design.md`.

---

## Step 1: The Weak Plan

### Goal
> "Get better at public speaking"

### Tactics (Weak)
1. Practice more
2. Watch TED talks
3. Maybe join a club
4. Do some presentations

---

## Step 2: Diagnosis

| Weakness | Problem | Rule Violated |
|----------|---------|---------------|
| "Practice more" | Not specific, no time block, not binary | Rule 2 (binary), Rule 3 (known time) |
| "Watch TED talks" | Passive input, not controllable outcome | Rule 1 (controllable) |
| "Maybe join a club" | Uncertain commitment, no deadline | Rule 1 (controllable), Rule 3 (known time) |
| "Do some presentations" | Vague quantity, no scheduling | Rule 2 (binary), Rule 3 (known time) |
| Goal itself | Not measurable, no "done" criteria | Planning criteria from `04-planning.md` |

**Execution prediction:** If this plan were executed, the user would score < 30% because no tactic is schedule-able or scorable.

---

## Step 3: The Transformation

### Goal (Redesigned)
> "Deliver 3 in-person presentations to live audiences in the next 12 weeks, and record average self-rated confidence > 7/10 across them."

Now the goal is specific, measurable, time-bound, and tied to an underlying vision (e.g., "I am a confident communicator who influences rooms").

### Tactics (Strong)

| Tactic | Type | Frequency | Duration | Why It Works |
|--------|------|-----------|----------|--------------|
| Rehearse next presentation out loud, alone | Recurring | 3×/week | 15 min | Fully controllable (Rule 1). Binary: did I rehearse? (Rule 2). Known time: 15 min (Rule 3). Small enough to start (Rule 4). |
| Record 1 practice session and review for filler words | Recurring | 1×/week | 20 min | Action-based. Creates feedback loop. |
| Book 1 speaking slot (meetup, work lunch, local club) | One-time | Week 2, 6, 10 | 30 min | Controllable. Binary: is it booked? (Rule 2). |
| Attend Toastmasters or local speaking club | One-time | Week 1 | 2 hours | Infrastructure/one-time setup. |
| Deliver presentation and self-rate confidence 1–10 | Recurring | Weeks 4, 8, 12 | 30 min | Directly tied to goal. Binary: done/not done. |

**Tactic count:** 5 total — within the 2–5 range per goal.

**Estimated weekly time:** ~1.5 hours — easy to schedule.

---

## Step 4: Calendar Scheduling

| Day | Time | Block | Activity |
|-----|------|-------|----------|
| Tue | 07:00–07:15 | Breakout | Rehearse presentation out loud |
| Thu | 07:00–07:15 | Breakout | Rehearse presentation out loud |
| Sat | 10:00–10:20 | Breakout | Record and review practice |
| Sun | 18:00–18:30 | Planning | Preview next week's presentation topic |

**Speaking slots (booked):**
- Week 4: Work lunch-and-learn
- Week 8: Local meetup
- Week 12: Toastmasters table topics

---

## Step 5: Scorecard Projection

| Week | Focus | Planned | Likely Done | Score |
|------|-------|---------|-------------|-------|
| 1 | Join club, book slot 1 | 3 | 3 | 100% |
| 2 | Rehearse, book slot 2 | 4 | 4 | 100% |
| 3 | Rehearse | 3 | 3 | 100% |
| 4 | Deliver presentation 1 | 4 | 3 | 75% |
| ... | ... | ... | ... | ... |

---

## Key Takeaways

1. **The goal must define "done."** "Get better" is not a goal. "Deliver 3 presentations with confidence > 7/10" is a goal.

2. **Tactics must be actions, not consumption.** "Watch TED talks" is consumption. "Rehearse out loud" is action.

3. **Controllable > optimal.** "Wait for a perfect speaking opportunity" is luck-dependent. "Book any slot by Tuesday" is controllable.

4. **Binary + scheduled = executable.** If a tactic cannot be placed on a calendar and scored yes/no, it is not a tactic. It is a wish.

5. **Start smaller than comfortable.** 15 minutes of rehearsal feels tiny. But 3×/week × 12 weeks = 36 practice sessions. That is transformational.

---

## Agent Redesign Script

When the user presents a weak plan, run this flow:

1. **Acknowledge** the goal as valid.
2. **Diagnose** which rules each tactic violates.
3. **Redesign** the goal using SMART criteria from `04-planning.md`.
4. **Generate** new tactics that pass all 6 Tactic Design Rules.
5. **Schedule** them into calendar blocks before the conversation ends.
6. **Predict** execution score: "With this plan, an average user scores 85%+."

