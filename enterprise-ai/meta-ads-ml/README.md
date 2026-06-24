# Petabyte-Scale Ads ML Platform — Meta (via Deloitte)

> Large-scale feature pipelines and user segmentation models optimizing ad targeting for 7M+ advertisers.

**Jun 2023 – Jun 2024 · Meta · Data Scientist via Deloitte**

## Overview

Engineered large-scale ML feature pipelines processing behavioral data at petabyte scale. Built user segmentation models and supervised classifiers to optimize ad targeting across Meta's advertiser ecosystem — delivering $100M+ in incremental revenue engagement.

## Impact

| Metric | Result |
|---|---|
| Revenue impact | $100M+ incremental engagement |
| Advertisers served | 7M+ |
| Data scale | Petabyte-scale behavioral data |
| Collaboration | Direct with Meta's Ads ML team |

## What Was Built

### Feature Pipelines (Petabyte Scale)
- Real-time and batch behavioral feature extraction from user interaction streams
- Feature store integration — consistent feature serving between training and inference
- Pipeline stack: Spark · Kafka · Airflow · Dataflow · Hive

### User Segmentation Models
- Embedding-based user clustering across behavioral dimensions (engagement, purchase intent, content affinity)
- Hierarchical segmentation with hundreds of micro-segments
- Online/offline consistency validation between training and serving distributions

### Supervised Ad Targeting Classifiers
- CTR and conversion probability models for ad auction scoring
- XGBoost + neural ranking models with GBDT feature importance analysis
- A/B testing framework for model rollout with revenue guardrails

## Architecture

```
Behavioral Event Stream (Petabyte/day)
        │
        ▼
┌──────────────────────────────────┐
│      Feature Pipeline            │
│  Kafka → Spark → Feature Store  │
│  (real-time + batch)             │
└──────────────┬───────────────────┘
               │
    ┌──────────┴──────────┐
    │                     │
┌───▼──────┐      ┌───────▼───────┐
│  User    │      │  Ad Targeting │
│  Segmen- │      │  Classifiers  │
│  tation  │      │  (CTR/CVR)    │
└───┬──────┘      └───────┬───────┘
    │                     │
    └──────────┬──────────┘
               │
        Ad Auction Scoring
        (7M+ Advertisers)
```

## Tech Stack

| Layer | Technology |
|---|---|
| Feature pipelines | Spark · Kafka · Airflow · Dataflow · Hive |
| ML frameworks | XGBoost · PyTorch · Scikit-learn |
| Feature store | Meta internal feature platform |
| Experimentation | Meta internal A/B testing framework |
| Infrastructure | Meta internal distributed compute |

## Demo

*Animated user segmentation clustering visualization on the [portfolio site](https://chuchugo.github.io/ai-ml-portfolio).*
