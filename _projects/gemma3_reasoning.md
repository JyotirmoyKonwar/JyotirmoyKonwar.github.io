---
layout: page
title: Teaching Gemma-3 to Reason
description: SFT + GRPO fine-tuning pipeline that improves reasoning in Gemma-3.
img: assets/img/9.jpg
importance: 1
category: LLM Training
giscus_comments: false
---

Architected a 3-stage **SFT + GRPO** fine-tuning pipeline for **Gemma-3**, driving a **12% gain in answer accuracy** and a **47% surge in reasoning quality**.

- Developed a custom composite reward function with weighted objectives (logical coherence, mathematical precision, strict XML compliance) that shapes model behavior directly at the reward-signal level.
- Reduced trainable parameters with **LoRA adapters** and accelerated training with custom JIT-compiled loops.

### Tech Stack

- Python, JAX, Tunix, Gemma-3, GRPO, LoRA

### Links

- **GitHub Repository**: [Tunix_Gemma3](https://github.com/JyotirmoyKonwar/Tunix_Gemma3)
