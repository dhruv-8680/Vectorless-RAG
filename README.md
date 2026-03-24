# Vectorless RAG

**RAG without vectors.** A retrieval-augmented generation system that replaces vector databases with hierarchical markdown indexes. Two specialized agents — one for ingestion, one for search — connected only by the file system. Swap any LLM, debug by reading files, deploy by copying a folder.

> Vectorless retrieval has always been there. LLMs just made it worth revisiting.

---

## How It Works

Traditional RAG embeds documents into vectors and runs similarity search. Vectorless RAG builds human-readable markdown indexes that an LLM navigates like a library catalog.

```
User Query
  → Master Index (which documents?)
    → Document Index (which chunks?)
      → Chunks (read & synthesize answer)
```

---

## The Two Agents

| Agent | Role | What It Does |
|---|---|---|
| **Ingestion Agent** | The Librarian | Reads documents, chunks text, extracts metadata via LLM, builds indexes |
| **Search Agent** | The Researcher | Reads indexes, identifies relevant chunks, synthesizes answers |

```
┌─────────────────┐                    ┌──────────────────┐
│ INGESTION AGENT │                    │  SEARCH AGENT    │
│ (The Librarian) │                    │ (The Researcher) │
├─────────────────┤                    ├──────────────────┤
│ Reads documents │                    │ Reads master     │
│ Chunks text     │                    │   index          │
│ Extracts meta   │──── files ────→    │ Reads doc indexes│
│ Builds indexes  │                    │ Reads chunks     │
│ Writes chunks   │                    │ Synthesizes      │
│                 │                    │   answer         │
└─────────────────┘                    └──────────────────┘
```

One writes. The other reads. Markdown is the contract between them.

---

## Knowledge Base Structure

```
/knowledge-base/
├── master-index.md                  ← Routes to the right document
│
├── /doc-001-ml-textbook/
│   ├── index.md                     ← Routes to the right chunks
│   ├── chunk-001.md
│   ├── chunk-002.md
│   └── chunk-003.md
│
├── /doc-002-python-guide/
│   ├── index.md
│   ├── chunk-001.md
│   └── chunk-002.md
```

| Level | File | Purpose |
|---|---|---|
| Master Index | `master-index.md` | One entry per document — source, type, topics, summary |
| Document Index | `<doc-folder>/index.md` | One entry per chunk — keywords, summary, organized by topic |
| Chunks | `chunk-NNN.md` | Actual content with frontmatter metadata |

---

## Key Features

- **Cross-LLM Plug and Play** — Knowledge base is plain markdown. Switch from Claude to GPT to Gemini to Llama — nothing breaks, nothing needs re-processing
- **Micro-Level Debugging** — Every retrieval decision is traceable through human-readable files. No similarity scores to interpret, no embedding visualizations needed
- **No Re-ingestion** — Change LLMs, improve summaries, reorganize topics — all without reprocessing source documents. Content and metadata are cleanly separated
- **Zero Infrastructure** — No vector database, no embedding service, no managed hosting. Git for version control, copy for backup
- **Best-Guess Answers** — The search agent never returns "no info found." It finds the closest match and clearly indicates confidence level

---

## Cost Model

This is **not a free solution**. It shifts costs from infrastructure to LLM inference.

| | Vector RAG | Vectorless RAG |
|---|---|---|
| Infrastructure | Vector DB hosting (monthly) | None |
| Per-query cost | Embedding + search + generation | Multiple LLM reads + generation |
| Model switch | Full re-embedding | Zero |
| Debugging | Opaque | Read the files |

Best suited for moderate query volumes where transparency, portability, and flexibility matter more than per-query cost at scale.

---

## When to Use

**Good fit:**
- Small to medium corpus (dozens to hundreds of documents)
- Need to audit or explain retrieval decisions
- Multiple LLM providers, no lock-in
- Documents change frequently
- Prototyping — working RAG in hours, not days

**Not ideal for:**
- Millions of documents
- Sub-second latency requirements
- High-volume concurrent queries where per-query cost dominates

---

## Project Structure

```
/
├── .claude/
│   └── commands/
│       ├── kb-ingestion.md          ← Ingestion agent skill
│       └── kb-search.md             ← Search agent skill
│
├── knowledge-base/                  ← All indexed data lives here
│   ├── master-index.md
│   ├── /doc-001-<name>/
│   │   ├── index.md
│   │   ├── chunk-001.md
│   │   └── ...
│   └── /doc-002-<name>/
│       ├── index.md
│       └── ...
│
├── sample-docs/                     ← Example documents for testing ingestion
│
└── README.md
```

| Path | Description |
|---|---|
| `.claude/commands/kb-ingestion.md` | Custom skill — ingestion agent that processes documents, extracts metadata, and builds the index hierarchy |
| `.claude/commands/kb-search.md` | Custom skill — search agent that navigates indexes, retrieves chunks, and synthesizes answers |
| `knowledge-base/` | Generated knowledge base — master index, document folders, document indexes, and chunks |
| `sample-docs/` | Example documents to test the ingestion pipeline |

---

## License

Apache 2.0
