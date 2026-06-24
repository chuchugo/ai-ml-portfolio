# Kubernetes Observability Platform & Elasticsearch — Alibaba Cloud

> Zero-to-one product launches: integrated K8s observability suite and Elasticsearch tooling that became Alibaba's internal gold standard for developer tooling.

**Jun 2020 – Sep 2020 · Alibaba Cloud · Product Manager**

## Overview

Drove a fundamental organizational mindset shift from reactive cloud infrastructure tooling to proactive observability. Designed an integrated Kubernetes observability product covering logs, metrics, and APM — which became the internal gold standard for developer tooling at Alibaba. Owned two zero-to-one product launches on Alibaba Cloud Elasticsearch.

## Products Shipped

### 1. Kubernetes Observability Suite (Logs + Metrics + APM)

**The problem:** Engineering teams were firefighting — they discovered problems only after user-facing incidents. Existing tooling was siloed: logs in one system, metrics in another, traces nowhere.

**The product:** A unified observability dashboard integrating:
- **Logs** — structured log aggregation with full-text search powered by Elasticsearch
- **Metrics** — time-series metrics from Kubernetes control plane + workloads (Prometheus-compatible)
- **APM** — distributed tracing across microservices with flame graphs and dependency maps

**Outcome:** Adopted as internal gold standard for developer tooling at Alibaba. Teams shifted from mean-time-to-detect (MTTD) hours → minutes.

### 2. Alibaba Cloud Elasticsearch — Two Zero-to-One Launches

Owned the full product lifecycle (discovery → spec → launch) for two new Elasticsearch product features on Alibaba Cloud:

- **Resource Calculator** — interactive sizing tool for Elasticsearch clusters (shard count, node type, storage, replica configuration) to help engineers right-size deployments. See [Alibaba Cloud pricing calculator](https://www.alibabacloud.com/pricing-calculator) for the live tool.
- **Managed Index Lifecycle Management (ILM)** — UI-driven policy configuration for hot/warm/cold/delete index tiers, reducing storage costs for time-series data workloads.

## Product Design Process

```
Discovery                 Definition               Delivery
    │                         │                        │
User interviews      ──►  PRD + Wireframes  ──►   Engineering
(SRE + DevOps teams)      Job stories              collaboration
                           Metrics definition        Beta program
                           Competitive analysis       GA launch
```

## Key Decisions

**Why unified vs. best-of-breed?** Context switching between 3+ tools adds 15–20 minutes to every incident response. A unified pane of glass trades some flexibility for dramatically faster MTTD/MTTR — the right call for Alibaba's internal developer audience.

**Why Elasticsearch for logs?** At Alibaba's scale, structured log search requires sub-second query latency on billions of events. Elasticsearch's inverted index architecture and native Alibaba Cloud integration made it the right substrate.

## Links

- [Alibaba Cloud Elasticsearch](https://www.alibabacloud.com/product/elasticsearch)
- [Alibaba Cloud Pricing Calculator](https://www.alibabacloud.com/pricing-calculator) — includes Elasticsearch cluster sizing
- [Alibaba Cloud Container Service (ACK)](https://www.alibabacloud.com/product/kubernetes) — the K8s platform this observability product was built on

## Demo

*Animated K8s node health grid + Elasticsearch metrics + APM trace waterfall on the [portfolio site](https://chuchugo.github.io/ai-ml-portfolio).*
