# Traffic Flow Prediction — Honda R&D Lab

> Using vehicle sensing telemetry to predict traffic flow at city scale.

## Overview

At Honda R&D Lab, built ML systems that ingest real-time vehicle sensor data to predict traffic flow patterns and support intelligent traffic management decisions. The system processes thousands of sensor streams simultaneously to generate short- and long-horizon traffic forecasts.

## Problem

Urban traffic management relies on static models and lagging indicators. Vehicle-embedded sensors offer a dense, real-time data signal that — when processed correctly — can predict congestion 10–20 minutes ahead.

## Approach

```
Vehicle Sensors ──► Ingestion Pipeline ──► Feature Engineering
                                                  │
                                    ┌─────────────▼──────────────┐
                                    │   Time-Series Forecasting  │
                                    │   (Temporal Fusion + GNN)  │
                                    └─────────────┬──────────────┘
                                                  │
                                    Traffic Management System
                                    (Signal Timing · Routing)
```

## Tech Stack

| Layer | Technology |
|---|---|
| Data Ingestion | Apache Kafka · Vehicle CAN bus |
| Feature Store | Time-series feature extraction |
| Model | Temporal Fusion Transformer + Graph Neural Network |
| Serving | Real-time inference < 200ms latency |
| Evaluation | MAPE, RMSE on 5/10/20-min horizons |

## Results

- **94%+ accuracy** on 10-minute traffic flow prediction
- Processes **50k+ sensor readings/second**
- Reduced average intersection wait time in test corridor by ~18%

## Demo

*Animated city-grid traffic simulation available on the [portfolio site](https://chuchwu.github.io).*
