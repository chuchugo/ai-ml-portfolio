# Prescription Insights GenAI Chatbot — Precision Growth

> RAG-powered chatbot delivering real-time prescription insights for medical practitioners.

## Overview

Built a production GenAI chatbot for Precision Growth that gives medical practitioners instant, grounded answers about drug prescriptions, contraindications, and clinical guidelines — all backed by live retrieval from authoritative sources.

## Problem

Physicians and practitioners make prescription decisions under time pressure. Existing drug reference tools are keyword-search-based, slow, and don't synthesize across multiple guidelines. A conversational AI with retrieval grounding addresses all three gaps.

## System Design

```
Practitioner Query
        │
        ▼
┌───────────────┐
│  Query        │  Intent classification + entity extraction
│  Understanding│  (drug names, patient context, question type)
└───────┬───────┘
        │
        ▼
┌───────────────────────────────────────┐
│            RAG Pipeline               │
│                                       │
│  ┌──────────┐  ┌──────────────────┐  │
│  │ Semantic │  │  Keyword (BM25)  │  │
│  │  Search  │  │     Search       │  │
│  └────┬─────┘  └────────┬─────────┘  │
│       └────────┬─────────┘           │
│          Hybrid Rerank               │
│       (Cohere Reranker)              │
└───────────────┬───────────────────────┘
                │
        Retrieved Context
                │
        ┌───────▼────────┐
        │   LLM Answer   │  Claude — grounded generation
        │   Generation   │  with citation pointers
        └───────┬────────┘
                │
        Practitioner Response
        + Source Citations
```

## Knowledge Sources

| Source | Content | Update Frequency |
|---|---|---|
| FDA Drug Database | Approved indications, contraindications, black box warnings | Weekly sync |
| PubMed | Recent clinical evidence (2020–present) | Daily |
| Drug Interactions DB | Interaction severity matrix | Weekly |
| Clinical Trial Registry | Active trials, off-label evidence | Weekly |
| EMR Templates | Local formulary & prescribing patterns | Real-time |

## Key Features

- **Grounded responses** — every answer cites the specific source passage
- **Contraindication alerts** — proactive flagging even when not asked
- **Patient-context aware** — adjusts recommendations based on age, renal function, comorbidities mentioned in query
- **Audit trail** — every interaction logged for compliance and QA review

## Tech Stack

- **LLM:** Claude claude-sonnet-4-6 via Anthropic API
- **Vector Store:** Pinecone (768-dim embeddings)
- **Reranker:** Cohere Rerank v3
- **Backend:** FastAPI · Python
- **Frontend:** React chat interface
- **Infra:** AWS ECS · RDS (audit logs)

## Guardrails

- Responses always include "Consult your pharmacist/specialist for final clinical decisions"
- Out-of-scope queries (non-prescription topics) gracefully declined
- Confidence threshold — low-confidence answers escalate to human review queue

## Demo

*Animated RAG chatbot conversation loop on the [portfolio site](https://chuchwu.github.io).*
