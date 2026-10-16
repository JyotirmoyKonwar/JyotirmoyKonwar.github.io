---
layout: page
title: DarkGuardRL
description: Self-play reinforcement learning for dark pattern detection with Qwen3-4B.
img: assets/img/8.jpg
importance: 2
category: LLM Training
giscus_comments: false
---

Fine-tuned **Qwen3-4B** with **SFT + GRPO** on a custom RL environment for dark pattern detection.

- Designed a Gym-compatible RL simulation environment with discrete, verifiable reward functions for dynamic adversarial decision-making.
- Implemented self-play policy optimization with GRPO, achieving a **+30–50 ELO improvement** over baseline within 500 training steps.
- Formulated strict multi-objective reward shaping that minimized false positives and eliminated invalid action paths during rollout.

### Tech Stack

- Python, PyTorch, Hugging Face TRL, GRPO, Qwen3

### Links

- **GitHub Repository**: [Eno_E](https://github.com/JyotirmoyKonwar/Eno_E)
