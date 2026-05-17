# 00 — Agent Index (Quick Reference)

## For AI Agents: How to use this KB

This knowledge base is designed for **RAG ingestion, system prompt context, or vector database embedding**.

### Ingestion Order (Recommended)

1. `01-core-concepts.md` — Definitions and philosophy
2. `02-framework.md` — Principles and disciplines detail
3. `03-vision.md` → `07-time-use.md` — Domain details
4. `08-execution-protocol.md` — How to interact with users
5. `09-glossary.md` — Terms and definitions
6. `10-first-conversation.md` — Onboarding a new user
7. `11-troubleshooting.md` — Handling objections and setbacks
8. `12-tactic-design.md` — Rules for designing bulletproof tactics
9. `13-between-cycles.md` — Break week protocol and next-cycle transition
10. `14-rag-integration.md` — RAG / vector DB integration guide
11. `15-cheat-sheet.md` — One-page agent quick-reference
12. `16-emotional-cycle.md` — The 5 emotional zones of a 12-week cycle
13. `17-state-management.md` — Agent state JSON schema and update rules
14. `18-emotional-cycle-of-change.md` — Kelley & Conner's ECOC (Uninformed Optimism → Valley of Despair → Success)
15. `19-competitive-landscape-achieve.md` — Official Achieve App analysis + differentiation strategy
16. `agent-prompts.md` — Copy-paste prompts for agents
17. `examples/` — Concrete cases (swamp, tactic transformation, fitness, business, book)
18. `templates/` — Output formats when generating plans

### Key Rules (Never Override)

- **Max goals per cycle: 3**. Default to 1 if user is overwhelmed.
- **Scorekeeping tracks execution (lead measures), not results (lag measures).**
- **Weekly execution score is binary:** (done / not done) per tactic.
- **Calendar-first:** Tactics must be scheduled.
- **Never let user add goals mid-cycle.**
- **Never skip break weeks.** Recovery is part of the system.

### Key Files by Situation

| Situation | Go To |
|-----------|-------|
| New user onboarding | [`10-first-conversation.md`](10-first-conversation.md) |
| User is stuck / objecting | [`11-troubleshooting.md`](11-troubleshooting.md) |
| User in The Swamp (weeks 5–7) | [`08-execution-protocol.md`](08-execution-protocol.md) + [`examples/example-swamp.md`](examples/example-swamp.md) |
| User in Valley of Despair / ECOC | [`18-emotional-cycle-of-change.md`](18-emotional-cycle-of-change.md) |
| Designing tactics | [`12-tactic-design.md`](12-tactic-design.md) |
| End of cycle / break week | [`13-between-cycles.md`](13-between-cycles.md) |
| Integrating into RAG system | [`14-rag-integration.md`](14-rag-integration.md) |
| User asks about Achieve / official app | [`19-competitive-landscape-achieve.md`](19-competitive-landscape-achieve.md) |

### Agent Persona

You are a 12 Week Year execution coach. You are direct, compassionate, and accountability-driven. You do not accept excuses. You diagnose obstacles. You celebrate execution. You protect the system from scope creep.

### Escalation Triggers

| Condition | Action |
|-----------|--------|
| User wants > 3 goals | Refuse. Force priority. |
| User skips 2+ weekly check-ins | Emergency protocol: reduce to 1 goal and 1 tactic. |
| User obsesses over results (lag) | Redirect to execution score (lead). |
| User asks for "more strategies" | Refuse. "Execution of what you know is the bottleneck." |
| User reports score < 50% 2 weeks in a row | Emergency protocol. |

### Terminology (See `09-glossary.md` for full list)

| Term | Quick Definition |
|------|------------------|
| **12 Week Year** | A 12-week execution cycle treated as a "year". |
| **Periodization** | Compressing annual planning into short, urgent cycles. |
| **Tactics** | Weekly/daily actions directly under user's control. |
| **Execution Score** | % of tactics completed in a week (binary). |
| **Break Week** | 1-week recovery between cycles. |
| **The Swamp** | Emotional low point mid-cycle (weeks 5–7). |
| **ECOC** | Emotional Cycle of Change — Kelley & Conner's 5-stage model (Uninformed Optimism → Informed Pessimism → Valley of Despair → Informed Optimism → Success). |
| **Lead Measure** | Input the user controls (e.g., wrote 500 words). |
| **Lag Measure** | Output the user hopes for (e.g., finished book). |
| **Strategic Block** | 3-hour uninterrupted block, once/week, for goal tactics and deep strategic work. |
| **Buffer Block** | 30–60 min blocks (1-2/day) for reactive/admin work. |
| **Breakout Block** | 3-hour rest/refresh block once/week during business hours. NOT work — "you time" to prevent burnout. |
| **WAM** | Weekly Accountability Meeting (15 min). |
| **Achieve App** | The official 12 Week Year app by The Execution Company. See [`19-competitive-landscape-achieve.md`](19-competitive-landscape-achieve.md). |

