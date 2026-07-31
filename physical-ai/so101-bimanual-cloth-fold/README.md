# Bimanual Cloth Folding with SO-101 Arms — Mission Robotics / New Theory Hackathon

> Two SO-101 arms, four imitation-learning policies, one folded sweater.

## Overview

Built at the Mission Robotics / New Theory "Embodied Metal Hackathon" with a
five-person team: two SO-101 bimanual teleop rigs collected cloth-folding
demonstrations in parallel, merged into a shared dataset, and used to train
and A/B compare four imitation-learning policies — ACT, SmolVLA, MolmoAct2,
and pi0.5 — behind a single policy-agnostic serving endpoint.

## What Was Built

```
Cloth Folding Pipeline
├── Data collection     ~40 teleoperated episodes, 2x SO-101, 3 cameras, 30 FPS
├── Training            Modal GPU launcher, 4 policy architectures
├── Serving             Policy-agnostic chunk-serving endpoint on Modal
└── Rollout              Chunk-prefetching client, 30 FPS execution, Rerun viz
```

## Key Technologies

- **LeRobot** — dataset format, teleop recording, policy training
- **ACT / SmolVLA / MolmoAct2 / pi0.5** — four imitation-learning architectures trained and compared on the same task
- **Modal** — serverless GPU training and inference serving
- **Rerun** — live visualization of camera feeds, joint states, and action traces

## Debugging Highlights

- Traced a "the arm just does something weird" failure mode to a wire-unit vs.
  calibrated-degree mismatch between SO-101 recordings and the LeRobot export.
- Established that reusing third-party SO-100/SO-101 checkpoints is a
  domain-adaptation problem — camera keys, left/right assignment, and action
  normalization must match before fine-tuning on top of one.
- Used Rerun to compare reference dataset trajectories against live rollouts,
  separating calibration bugs from genuine generalization gaps.

## Key Learnings

- A serving layer that reads camera keys, state dimension, and normalization
  straight from the checkpoint config makes it cheap to A/B multiple policy
  architectures behind one endpoint.
- Returning whole action chunks per request (rather than one action per
  network round-trip) removes network latency from the control loop entirely.
- In imitation learning, correctness bugs and "not enough data" look identical
  from the outside — always rule out the former with visualization first.

## Links

- Project page with photos: [index.html](index.html)
- Standalone project repo: [chuchugo/so101-bimanual-cloth-fold](https://github.com/chuchugo/so101-bimanual-cloth-fold)
- Full LeRobot fork / commit: [yuyangch/ycsf@9b40b8a](https://github.com/yuyangch/ycsf/commit/9b40b8aebc6aa1327db20a9853b13afb9daeeb8d)
