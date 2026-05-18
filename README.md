# 12 Week Year — AI Agent Knowledge Base

Plug-and-play knowledge base for an AI agent that coaches users through the **12 Week Year** execution system by Brian P. Moran & Michael Lennington.

## Quick Start (3 steps)

1. **Load `agent/system-prompt.md`** into your agent's system prompt
2. **Chunk `knowledge/`** into a vector DB (500–800 tokens, 100-token overlap)
3. **Wire semantic triggers** to retrieve `agent/10-*`, `agent/11-*`, `agent/13-*`, and `rag/*` on demand

## Folder Structure

```
12-week-year-kb/
├── agent/          ← System prompt + on-demand protocols
│   ├── system-prompt.md          ← THE prompt (identity, rules, scripts, boundaries)
│   ├── 10-first-conversation.md  ← Onboarding (loaded on first contact)
│   ├── 11-troubleshooting.md     ← 10 tested objection responses
│   ├── 13-between-cycles.md      ← Break week & transition protocol
│   └── 17-state-management.md    ← JSON state schema (developer-facing)
├── rag/            ← Semantic recall — emotional models + competitive
│   ├── 14-rag-integration.md     ← How to embed this KB (developer-facing)
│   ├── 16-emotional-cycle.md     ← 5 emotional zones + zone-specific playbook
│   ├── 18-emotional-cycle-of-change.md  ← ECOC (Kelley & Conner model)
│   └── 19-competitive-landscape-achieve.md ← Achieve app analysis
├── knowledge/      ← Vector DB — domain, templates, examples
│   ├── 01-core-concepts.md       ← Periodization, cycle structure
│   ├── 02-framework.md           ← Accountability, Commitment, Greatness in the Moment
│   ├── 03-vision.md              ← 3-year vision crafting
│   ├── 04-planning.md            ← Goal criteria, tactics breakdown
│   ├── 05-process-control.md     ← WAM, daily check
│   ├── 06-measurement.md         ← Scorekeeping, lead vs lag
│   ├── 07-time-use.md            ← Strategic/buffer/breakout blocks
│   ├── 09-glossary.md            ← All 12WW term definitions
│   ├── 12-tactic-design.md       ← 6 rules for bulletproof tactics
│   ├── templates/                ← Reusable output structures
│   └── examples/                 ← Concrete cases (fitness, business, book, swamp)
├── README.md
└── kb-index.json
```

## Semantic Recall Triggers

| User says... | Retrieve |
|-------------|----------|
| New user, first contact | `agent/10-first-conversation.md` |
| "I don't have time / I failed / This doesn't work" | `agent/11-troubleshooting.md` |
| End of 12-week cycle | `agent/13-between-cycles.md` |
| "I lost motivation" / weeks 5–7 | `rag/16-emotional-cycle.md` |
| "Why is this so hard?" | `rag/18-emotional-cycle-of-change.md` |
| "What about the official Achieve app?" | `rag/19-competitive-landscape-achieve.md` |

## What Was Removed (v2.0 → v2.1)

- `agent-prompts.md` → absorbed into `system-prompt.md`
- `00-agent-index.md` → absorbed into `system-prompt.md`
- `08-execution-protocol.md` → absorbed into `system-prompt.md`
- `rag/15-cheat-sheet.md` → deleted (100% redundant with system prompt)

Result: **4 fewer files, ~50% less token overhead** for the system prompt layer.
