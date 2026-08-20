# Fast Loop · Self-Improving Robotics

**🏆 Top Winner — Physical AI Hackathon** hosted by NVIDIA × Nebius × Antioch × Toloka

> Can robots teach themselves to get better — recursively?  
> Fast Loop answers yes.

## Demo

[![Fast Loop Demo](https://img.youtube.com/vi/placeholder/0.jpg)](https://lnkd.in/gxRx5nmr)

▶ [Watch the full demo video](https://lnkd.in/gxRx5nmr)

## Results

| Metric | Fast Loop | Baseline | Delta |
|---|---|---|---|
| Held-out success | **83%** | 38% | **+46 pts** |
| Cup stacking preflight | 9/13 | — | — |
| Cube grasping preflight | 10/10 | — | — |

## What We Built

An end-to-end self-improving training loop for robotics — no human in the loop. The robot:

1. **Acts** using a System-1 VLA policy (SmolVLA / GR00T)
2. **Estimates uncertainty** — low uncertainty: execute; high uncertainty: escalate
3. **Gates** to a System-2 planner that re-plans and verifies the move in Antioch simulation
4. **Executes** the verified action chunk on the physical SO-101 arm
5. **Observes** the outcome — success/failure feeds back to step 1

Between runs, an offline loop fine-tunes the VLA with LoRA on Nebius GPU, generates edge cases via NVIDIA Cosmos, and evaluates with a Toloka-style harness.

## Architecture

```
━━━━━━━━━━━━━━━━ LIVE LOOP (runs on stage) ━━━━━━━━━━━━━━━━

1. Perception       RGB-D → state estimate
        │
        ▼
2. System-1 VLA     action + uncertainty
        │
   low uncertainty ────▶ 5. Action (Antioch sim / SO-101)
        │                          │
   high uncertainty                ▼
        ▼               6. Observe (outcome → back to 1)
3. Gate: trust or escalate?
        │
        ▼
4. System-2         re-plan + verify rollout in sim
        └──────────────▶ 5. Action

━━━━━━━━━━━━━━━━ OFFLINE (between runs) ━━━━━━━━━━━━━━━━━━━

Cosmos (NVIDIA)    → edge case generation, stress the gate
Nebius GPU         → LoRA fine-tune VLA, adapt to task
Toloka eval        → score + trust metric per episode

━━━━━━━━━━━━━━━━ SPONSOR MAP ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Antioch = sim env + verification rollout
Nebius  = compute + finetune
NVIDIA  = Cosmos scenarios + LeRobot / GR00T policy
Toloka  = eval harness framing
```

## Tech Stack

| Component | Technology |
|---|---|
| VLA Backbone | SmolVLA / GR00T (LeRobot) |
| Fine-tuning | LoRA on Nebius GPU |
| Simulation | Antioch 3D scene editor |
| Edge cases | NVIDIA Cosmos |
| Evaluation | Toloka-style harness |
| Hardware | SO-101 Robot Arm |
| Frontend | React (training dashboard) |

## Repository Branches

| Branch | Description |
|---|---|
| `main` | Core loop orchestration & entry point |
| `fast-loop-frontend` | Web dashboard for monitoring training iterations |
| `AntiochSim` | 3D simulation environment & scene editor |
| `opus-motion-planner` | System-2 motion planning & re-planner |
| `so101-vla-physical-integration` | SO-101 hardware bridge + VLA integration |

## Team

Built in 48 hours at the Physical AI Hackathon — NVIDIA × Nebius × Antioch × Toloka.

## Links

- [Portfolio project page](https://chuchugo.github.io/ai-ml-portfolio/physical-ai/fast-loop/)
- [Demo video](https://lnkd.in/gxRx5nmr)
- [Hackathon announcement](https://lnkd.in/p/gWvPEJyn)
