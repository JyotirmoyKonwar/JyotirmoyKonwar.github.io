---
layout: page
title: Tiny Stories Diffusion Language Model
description: A diffusion language model built from scratch to tell tiny stories.
img: assets/img/11.jpg
importance: 3
category: LLM Training
giscus_comments: false
---

Formulated and trained a discrete, **non-autoregressive diffusion language model** from scratch that replaces left-to-right decoding with parallel, confidence-based iterative token unmasking.

- Training pipeline with **SwiGLU** activations, **TikToken (BPE)** encoding, mask-token injection, and **Rotary Positional Embeddings (RoPE)** on the TinyStories dataset.
- Reached a perplexity of **18.88**, outperforming GPT-2's baseline score of 19.93.

### Tech Stack

- Python, PyTorch, Hugging Face

### Links

- **GitHub Repository**: [Tiny_Stories_Diffusion](https://github.com/JyotirmoyKonwar/Tiny_Stories_Diffusion)
- **Live Demo**: [Tiny_DiffLM_Story_Teller on Hugging Face Spaces](https://huggingface.co/spaces/Jyo-K/Tiny_DiffLM_Story_Teller/)
