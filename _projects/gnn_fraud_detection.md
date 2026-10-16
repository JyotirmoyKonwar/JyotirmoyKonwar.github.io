---
layout: page
title: LLM-Augmented GNN for Fraud Detection
description: Combining a fine-tuned SLM with a Skip-GNN for graph fraud detection.
img: assets/img/10.jpg
importance: 1
category: Machine Learning
giscus_comments: false
---

Recreated and extended the FLAG framework to resolve graph neighborhood camouflage in text-attributed anomaly detection.

- Alternating **PEFT/LoRA fine-tuning** of an SLM with a composite loss (BCE, KL-divergence, orthogonality), resolving context limits with **semantic k-hop neighbor sampling**.
- Dual-branch **Skip-GNN** with multi-head attention fusion on LLM-derived embeddings, outperforming **GCN/GAT** baselines by **5% AUC-ROC/F1** on imbalanced graph benchmarks.

### Tech Stack

- Python, PyTorch, PyTorch Geometric, Hugging Face, PEFT

### Links

- **GitHub Repository**: [LLM_Enhanced_GNN_Fraud_Detection](https://github.com/JyotirmoyKonwar/LLM_Enhanced_GNN_Fraud_Detection)
