# Physical AI Smart Factory — Deloitte × NVIDIA Alliance

> Exploring the frontier of Physical AI for next-generation manufacturing.

## Overview

Collaborated with Deloitte's NVIDIA Alliance and Smart Factory team to explore Physical AI architectures combining Vision-Language Models (VLM), Vision-Language-Action models (VLA), and World Foundation Models (WFM) for intelligent industrial automation.

## Key Technologies

- **NVIDIA Cosmos** — World Foundation Model for physical environment simulation and scene understanding
- **Isaac Sim** — Physics-accurate robot simulation and synthetic data generation
- **LeRobot** — End-to-end robot learning from demonstrations

## What Was Built

```
Smart Factory Pipeline
├── Scene Understanding     VLM-based object & anomaly detection
├── Action Planning         VLA for robot task decomposition
├── World Simulation        Cosmos-based environment modeling
└── Robot Execution         Isaac Sim → Real hardware bridge
```

## Architecture

```
Camera Feed ──► VLM (Scene Understanding)
                      │
              ┌───────▼────────┐
              │  World Model   │  ← NVIDIA Cosmos
              │  (Cosmos WFM) │
              └───────┬────────┘
                      │
              VLA Action Policy
                      │
              Isaac Sim Validation
                      │
              Robot Execution
```

## Demo

![Demo](../../projects/deloitte-nvidia/demo.html)

*Live animated demo available on the [portfolio site](https://chuchwu.github.io).*

## Key Learnings

- VLMs enable zero-shot scene understanding without task-specific training data
- World Foundation Models dramatically reduce sim-to-real transfer gap
- LeRobot's imitation learning pipeline cuts robot programming time by ~60%
