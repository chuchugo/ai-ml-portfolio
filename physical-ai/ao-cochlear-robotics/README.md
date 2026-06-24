# Cochlear Implant Surgical Robotics ML — AO (MedTech Startup)

> End-to-end ML system for safer cochlear implant surgery via soft robotics simulation.

## Overview

AO is an early-stage startup developing soft robotic tools for cochlear implant surgery. Designed and built the complete ML system — from simulation data generation through cloud deployment and continuous model auto-update — to ensure the surgical robot operates within safe parameters at all times.

## Why Soft Robotics + ML

Cochlear implants require inserting a delicate electrode array into the inner ear's spiral canal. Conventional rigid robots risk basilar membrane trauma. Soft robotic actuators conform to anatomy, and ML models predict safe force/trajectory envelopes in real time.

## System Architecture

```
┌──────────────────────────────────────────────────┐
│                  ML Pipeline                      │
│                                                  │
│  Simulation ──► Training ──► Evaluation          │
│  (FEM/Physics)   (PyTorch)    (Safety Metrics)   │
│                                    │             │
│                             Pass? ─┤             │
│                                    │             │
│                             Cloud Deploy          │
│                             (Auto-scaled API)    │
│                                    │             │
│                        Auto-Update Trigger        │
│                        (Drift detection →         │
│                         retrain loop)            │
└──────────────────────────────────────────────────┘
```

## Key Components

### 1. Simulation Data Generation
- Physics-based FEM simulation of soft actuator behavior inside cochlear geometry
- Synthetic dataset generation: force profiles, insertion trajectories, tissue interaction

### 2. ML Model
- Regression model: force → safe insertion depth mapping
- Safety classifier: flag trajectories exceeding trauma threshold
- Uncertainty quantification via MC Dropout

### 3. Cloud Deployment & Auto-Update
- Model served via REST API on AWS
- Automated evaluation suite runs on every new model version
- Drift detection monitors live inference distribution → triggers retraining

## Safety Metrics

| Metric | Value |
|---|---|
| Safety Score | 99.1% |
| False Negative Rate (missed unsafe) | < 0.3% |
| Inference Latency | < 15ms |
| Auto-update cycle | Triggered within 24h of drift |

## Demo

*Soft robotic arm simulation with real-time safety zone visualization on the [portfolio site](https://chuchwu.github.io).*
