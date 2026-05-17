# 12 Week Year — AI Agent Knowledge Base

Plug-and-play knowledge base for an AI agent that coaches users through the **12 Week Year** execution system by Brian P. Moran & Michael Lennington.

## Folder Structure

```
12-week-year-kb/
├── agent/          ← System prompt — loaded at inference
├── rag/            ← Semantic recall — trigger-based retrieval
├── knowledge/      ← Vector DB — chunked & embedded
├── README.md       ← This file
└── kb-index.json   ← Machine-readable KB manifest
```

### `agent/` — System Prompt (6 files)

Fichiers chargés dans le system prompt au moment de l'inférence. Définissent le persona, les règles, les protocoles d'interaction et l'état multi-semaine.

| Fichier | Rôle |
|---------|------|
| `agent-prompts.md` | Prompts système copy-paste pour l'agent |
| `00-agent-index.md` | Référence rapide : règles, persona, déclencheurs d'escalade |
| `08-execution-protocol.md` | Manuel opérationnel : parcours utilisateur, check-in hebdomadaire |
| `10-first-conversation.md` | Protocole d'onboarding pas-à-pas |
| `11-troubleshooting.md` | Réponses testées aux 10 objections les plus courantes |
| `13-between-cycles.md` | Protocole de semaine de pause et transition |
| `17-state-management.md` | Schéma JSON de l'état agent et règles de mise à jour |

### `rag/` — Semantic Recall (5 files)

Fichiers récupérés par recherche sémantique selon le déclencheur utilisateur. Pas chargés par défaut.

| Fichier | Déclencheur |
|---------|-------------|
| `14-rag-integration.md` | Guide pour intégrer la KB dans un système RAG/vector DB |
| `15-cheat-sheet.md` | Aide-mémoire une page avant les check-ins |
| `16-emotional-cycle.md` | Les 5 zones émotionnelles + playbook par zone |
| `18-emotional-cycle-of-change.md` | Modèle ECOC de Kelley & Conner (5 étapes psychologiques) |
| `19-competitive-landscape-achieve.md` | Analyse de l'app officielle Achieve + stratégie de différenciation |

### `knowledge/` — Vector DB (14 files)

Fichiers chunkés et embeddés dans une base vectorielle. Contenu domaine pur — concepts, templates, exemples.

| Fichier | Contenu |
|---------|---------|
| `01-core-concepts.md` | Periodization, structure de cycle, équation de performance |
| `02-framework.md` | Accountability, Commitment, Greatness in the Moment |
| `03-vision.md` | Vision 3 ans, protocole de brain-storming |
| `04-planning.md` | Critères de goal, décomposition en tactiques |
| `05-process-control.md` | WAM, planification hebdomadaire, check quotidien |
| `06-measurement.md` | Scorekeeping, lead vs lag measures |
| `07-time-use.md` | Strategic block, buffer block, breakout block |
| `09-glossary.md` | Définitions alphabétiques de tous les termes |
| `12-tactic-design.md` | Les 6 règles pour des tactiques bulletproof |
| `templates/12-week-plan-template.md` | Structure de sortie pour un plan 12 semaines |
| `templates/weekly-plan-template.md` | Structure de sortie pour le plan d'une semaine |
| `examples/example-fitness.md` | Exemple : remise en forme |
| `examples/example-business.md` | Exemple : croissance business solopreneur |
| `examples/example-book.md` | Exemple : écrire un livre en 12 semaines |
| `examples/example-swamp.md` | Exemple : gestion du Swamp (semaines 5–7) |
| `examples/example-tactic-transformation.md` | Exemple : transformation tactique faible → forte |

## Key Rules (Never Override)

- **Max goals per cycle: 3**. Default to 1 if user is overwhelmed.
- **Scorekeeping tracks execution (lead measures), not results (lag measures).**
- **Weekly execution score is binary:** (done / not done) per tactic.
- **Calendar-first:** Tactics must be scheduled.
- **Never let user add goals mid-cycle.**
- **Never skip break weeks.** Recovery is part of the system.

## Agent Persona

You are a 12 Week Year execution coach. Direct, compassionate, accountability-driven. You do not accept excuses. You diagnose obstacles. You celebrate execution. You protect the system from scope creep.

## Ingestion Quick-Start

1. **Agent layer** → Load all `agent/*.md` into system prompt
2. **Knowledge layer** → Chunk all `knowledge/*.md` into vector DB (500–800 tokens, 100-token overlap)
3. **RAG layer** → Set up semantic triggers to retrieve `rag/*.md` files on specific user queries

See [`rag/14-rag-integration.md`](rag/14-rag-integration.md) for detailed chunking strategy and metadata schema.
