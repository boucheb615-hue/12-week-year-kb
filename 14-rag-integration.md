# 14 — RAG Integration Guide

## Goal

This knowledge base is designed to be **ingested by any RAG (Retrieval-Augmented Generation) system** or embedded into an agent's system prompt for plug-and-play coaching.

---

## Ingestion Options

### Option A: Full Context Injection (Small Models / Short Conversations)

Load the entire KB into the system prompt. This works with agents that have long context windows (128K+ tokens) or for localized use.

**Steps:**
1. Concatenate all `.md` files in ingestion order (see `00-agent-index.md`).
2. Add the system prompt from `agent-prompts.md` at the top.
3. Truncate examples if token budget is tight. Keep core concepts, framework, execution protocol, and one example.

**Recommended priority order if space is limited:**
1. `agent-prompts.md` (system prompt)
2. `00-agent-index.md` (rules + persona)
3. `01-core-concepts.md`
4. `08-execution-protocol.md`
5. `12-tactic-design.md`
6. `11-troubleshooting.md`
7. One example file (pick relevant to user's domain)

### Option B: Vector Database (Large Scale / Multi-User)

Chunk the KB into semantic units and embed into a vector DB (Pinecone, Weaviate, Chroma, etc.).

**Chunking Strategy:**
- Chunk by section header (H2 / H3)
- Preserve file context in metadata: `source_file`, `topic`, `ingestion_priority`
- Chunk size: 500–800 tokens with 100-token overlap

**Metadata fields per chunk:**
```json
{
  "source_file": "04-planning.md",
  "section": "Tactics Breakdown",
  "topic": "planning",
  "ingestion_priority": 6,
  "file_type": "core"
}
```

**Query routing:**
- User says "I missed a week" → query `11-troubleshooting.md`
- User says "How do I set a goal?" → query `04-planning.md`
- User says "I don't feel like it" → query `02-framework.md` + `11-troubleshooting.md`

### Option C: Hierarchical Prompt Assembly (Medium Scale)

Keep the KB as files and assemble prompts dynamically based on user state.

**State-based assembly:**
| User State | Files to Inject |
|------------|----------------|
| New user, first conversation | `10-first-conversation.md`, `03-vision.md`, `04-planning.md`, `agent-prompts.md` |
| Weekly check-in | `08-execution-protocol.md`, `06-measurement.md` |
| Score < 50% | `08-execution-protocol.md` (emergency), `11-troubleshooting.md`, `05-process-control.md` |
| User in The Swamp / Valley of Despair | `18-emotional-cycle-of-change.md`, `16-emotional-cycle.md`, user's vision |
| Break week | `13-between-cycles.md`, `09-glossary.md` |
| Designing tactics | `12-tactic-design.md`, `04-planning.md`, `examples/` |
| User asks about Achieve / official app | `19-competitive-landscape-achieve.md` |
| Integrating into RAG system | `14-rag-integration.md` |

---

## System Prompt Construction

Here is a minimal but complete system prompt using this KB:

```
You are a 12 Week Year execution coach.

CONTEXT:
[Insert 00-agent-index.md]
[Insert 01-core-concepts.md]
[Insert 08-execution-protocol.md]
[Insert 12-tactic-design.md]
[Insert 11-troubleshooting.md]

RULES:
- Max 1–3 goals per 12-week cycle. Default to 1.
- Execution score is binary: (done / not done).
- Track lead measures (actions), not lag measures (results).
- Tactics must be scheduled in calendar.
- Never add goals mid-cycle.

When a user says "I don't have time," run a time-use audit.
When a user says "I don't feel like it," remind them of commitment.
When a user asks for "more strategies," refuse: "Execution is the bottleneck."

Use examples from the KB when the user is stuck.
Use templates when generating plans.
Follow the weekly check-in script every week.
```

---

## Multi-Language Note

This KB is written in English. For non-English users:
- Ingest the KB in English.
- Instruct the agent to translate all output to the user's language.
- Keep technical terms ("Execution Score," "Tactics," "The Swamp") in English with a brief translation in parentheses on first use.
- The structure and logic are language-agnostic.

---

## Maintenance

When updating this KB:
1. Keep filenames stable (agents may reference them).
2. Update `kb-index.json` when adding/removing files.
3. Update `00-agent-index.md` ingestion order when adding new core files.
4. Add new objections to `11-troubleshooting.md` when discovered.
5. Add new examples to `examples/` when new domains are supported.

