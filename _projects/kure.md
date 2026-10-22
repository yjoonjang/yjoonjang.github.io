---
layout: page
title: KURE
description: Korea University Retrieval Models: dense, multi-vector, sparse, and reranker models for Korean retrieval.
importance: 2
category: research
github: https://github.com/nlpai-lab/KURE
---

Led the lab's flagship Korean-English retrieval project, built the MTEB-Ko-Retrieval Leaderboard, and open-sourced the model family and training/evaluation code, reaching **250+ GitHub stars**.

- **Dense & Multi-Vector:** Developed KURE-v1, KURE-v2, and KURE-v3. KURE-v1 and KURE-v2 both ranked 1st on the leaderboard (as of Aug. 2025 and Oct. 2026, respectively). KURE-v1 surpassed 3M downloads, KURE-v2, a multi-vector model, outperforms 8B dense models while being 50× smaller, and KURE-v3 outperforms Qwen3-Embedding-8B while being 7× smaller and is served through a public API
- **Sparse:** KURE-Sparse-{base, nano}, state-of-the-art Korean sparse retrieval overall and under 0.5B parameters, respectively. The base model also outperforms 8B dense models
- **Reranker:** KURE-Reranker-{base, nano}, state-of-the-art Korean reranking performance under 4B and 1B parameters, respectively. The 149M nano delivers 19.5× the throughput of Qwen3-Reranker-4B with only a 1.5-point gap in nDCG@10

[GitHub](https://github.com/nlpai-lab/KURE) | [HF](https://huggingface.co/collections/nlpai-lab/kure) | [API](https://kure.kullm.ai/)
