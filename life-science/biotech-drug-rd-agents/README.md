# Multi-Agent Drug R&D Accelerator — Biotech

> Deep multi-agent systems to accelerate pharmaceutical research and development.

## Overview

Built a multi-agent AI system that parallelizes and automates the most time-consuming parts of drug R&D: literature search, clinical document review, and regulatory document generation. The system compresses weeks of analyst work into hours.

## Agent Architecture

```
                    ┌─────────────────┐
                    │  Orchestrator   │
                    │    (Planner)    │
                    └────────┬────────┘
           ┌─────────────────┼─────────────────┐
           │                 │                 │
    ┌──────▼──────┐  ┌───────▼──────┐  ┌──────▼──────┐
    │   Search    │  │    Review    │  │   DocGen    │
    │   Agent     │  │    Agent     │  │   Agent     │
    │             │  │              │  │             │
    │ PubMed      │  │ Evidence     │  │ ICH/FDA     │
    │ ClinTrials  │  │ Grading      │  │ Templates   │
    │ Patents     │  │ Contradiction │  │ CTD Format  │
    └──────┬──────┘  └───────┬──────┘  └──────┬──────┘
           └─────────────────┼─────────────────┘
                    ┌────────▼────────┐
                    │  Synthesis      │
                    │  Agent          │
                    │  (Final Report) │
                    └─────────────────┘
```

## Capabilities

### Search Agent
- Queries PubMed, ClinicalTrials.gov, patent databases
- Semantic search with embedding-based re-ranking
- Deduplication and relevance scoring

### Review Agent
- Evidence grading (Oxford LoE framework)
- Contradiction detection across sources
- Structured data extraction from unstructured papers

### DocGen Agent
- Clinical Study Report (CSR) generation
- ICH E3 / CTD Module 5 compliant formatting
- Auto-populated from structured review outputs

### Synthesis Agent
- Cross-agent information integration
- Gap analysis and recommendation generation
- Executive summary for non-technical stakeholders

## Tech Stack

- **Orchestration:** LangGraph multi-agent framework
- **LLM:** Claude claude-sonnet-4-6 (main reasoning) + Haiku (classification tasks)
- **RAG:** Pinecone vector store + BM25 hybrid retrieval
- **Document generation:** Structured output → Pandoc → DOCX/PDF

## Impact

- Literature review time: **weeks → hours**
- Document drafting: **days → minutes**
- Evidence coverage: **3× more sources** reviewed vs manual process

## Demo

*Live multi-agent graph animation on the [portfolio site](https://chuchwu.github.io).*
