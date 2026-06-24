# NL-to-SQL Marketing Analytics AI — Apple (via Deloitte)

> LLM-powered system converting natural language to validated SQL for real-time ROAS/ROI insights.

**Jun 2024 – Dec 2025 · Apple · AI Consultant via Deloitte**

## Overview

Built an LLM-powered marketing analytics system that lets Apple's global marketing teams query campaign performance data in plain English — no SQL knowledge required. The system generates validated SQL, executes against Apple's internal data warehouse, and returns deterministic ROAS/ROI insights with sub-4-second response time.

## Impact

| Metric | Result |
|---|---|
| Revenue impacted | $3M+ across 100+ global campaigns |
| Response time | < 4 seconds end-to-end |
| Query accuracy | Deterministic, validated outputs |
| Campaigns improved | 100+ globally |

## System Architecture

```
User (Natural Language)
        │
        ▼
┌───────────────────┐
│  Intent Parser    │  Entity extraction: metrics, dimensions, filters, timeframes
│  (LLM)           │
└────────┬──────────┘
         │
┌────────▼──────────┐
│  SQL Generator    │  Schema-aware query construction
│  (LLM + Schema)  │  Table/column grounding against Apple data warehouse
└────────┬──────────┘
         │
┌────────▼──────────┐
│  Validation Layer │  Syntax check · semantic validation · safety guardrails
│                   │  Rejects queries that could cause full-table scans or PII leakage
└────────┬──────────┘
         │
┌────────▼──────────┐
│  Execution        │  Apple internal data warehouse (BigQuery-compatible)
│  + Formatting     │  ROAS · ROI · CTR · CPC formatted for business users
└───────────────────┘
```

## Key Technical Challenges

### 1. Deterministic Outputs
Marketing decisions require reproducible numbers. Addressed via:
- Temperature=0 inference for SQL generation
- Post-generation validation pipeline that rejects ambiguous or non-deterministic queries
- Schema pinning — model grounded to exact table/column definitions, not inferred

### 2. Query Validation Pipeline
- SQL syntax validation before execution
- Semantic consistency check (does the query match the user's stated intent?)
- Row-count safeguards to prevent accidental full-table scans
- PII field blocklist enforced at validation layer

### 3. Schema Grounding
Apple's data warehouse spans hundreds of tables. Used RAG-based schema retrieval — embedding table/column descriptions and retrieving the most relevant subset per query — reducing hallucinated column names to near zero.

## Tech Stack

| Component | Technology |
|---|---|
| LLM | GPT-4 (SQL generation) |
| Schema retrieval | RAG — vector search over schema embeddings |
| Validation | Python rule engine + LLM semantic check |
| Data warehouse | Apple internal (BigQuery-compatible) |
| API | FastAPI · deployed on Apple internal infra |

## Demo

*Animated NL → SQL → results flow on the [portfolio site](https://chuchuwu.github.io/ai-ml-portfolio).*
