---
layout: page
title: Projects
permalink: /projects/
description: Research projects in NLP, Information Retrieval, and RAG.
nav: false
---

## WBL: World Best LLM Project

- Led the data team and established a query clarity evaluation framework using engineered GPT-5.2 prompts, training a Qwen3-4B model as a proprietary tagger to selectively curate datasets with diverse clarity levels.
- Established a robust response filtering pipeline for off-policy SFT data by ensembling three distinct reward models, applying score fusion techniques to accurately evaluate and retain high-quality responses.
- Curated and refined large-scale alignment samples by integrating the score fusion pipeline with rigorous LLM-as-a-judge and Code Execution metrics to effectively eliminate repetitive and low-quality responses.

---

## [KURE: Korea University Retrieval Embedding Model](https://github.com/nlpai-lab/KURE) &nbsp; [GitHub](https://github.com/nlpai-lab/KURE) \| [HuggingFace](https://huggingface.co/nlpai-lab/KURE-v1)

- Led the lab's flagship Korean retrieval project; curated large-scale training datasets and trained a dense retriever that achieved **State-of-the-Art (1st place) on the MTEB-ko-retrieval leaderboard** (as of Aug. 2025).
- Designed and maintained `MTEB-ko-retrieval`, establishing a comprehensive evaluation suite and standardized public leaderboard for the Korean IR community.
- Open-sourced the framework, achieving **200+ GitHub stars and 1.1M+ cumulative downloads** on Hugging Face.
- **Awarded Best Oral Presentation at HCLT 2025.**

---

## Korean ColBERT & Sparse Retrievers &nbsp; [colbert-ko-v1](https://huggingface.co/yjoonjang/colbert-ko-v1) \| [splade-ko-v1](https://huggingface.co/yjoonjang/splade-ko-v1) \| [inference-free-splade-ko-v1](https://huggingface.co/yjoonjang/inference-free-splade-ko-v1)

- Trained and open-sourced Korean ColBERT and SPLADE variants, achieving **State-of-the-Art performance among corresponding architectures** (as of Feb. 2026) on the Korean Retrieval Benchmark.
- Outperformed existing multilingual and Korean fine-tuned models, providing highly optimized, reproducible pipelines to advance dense-sparse hybrid retrieval experiments.

---

## KT-Korea University Collaborative Research (Korean Legal LLM)

- Developed an end-to-end training recipe for a Korean legal-domain LLM; defined real-world judicial tasks, curated expert-written and synthetic alignment datasets, and optimized training strategies to preserve general capabilities.
- This research directly contributed to KT winning a **$10.42 million contract** to build an AI platform for the South Korean Supreme Court. [[News](https://www.koreatimes.co.kr/business/tech-science/20250721/judiciary-meets-ai-kt-to-build-ai-platform-for-court-system)]
- Published the training methodologies and data pipelines as **LEGALMIDM** at the ICLR 2026 Data-FM Workshop.

---

## [PreRanker](https://github.com/yjoonjang/PreRanker) &nbsp; [GitHub](https://github.com/yjoonjang/PreRanker) \| [HuggingFace](https://huggingface.co/yjoonjang/preranker-v1)

- Built a lightweight reranker to narrow down candidate tools, reducing tool-call scope for LLM agents.

---

## URACLE-Korea University Collaborative Research

- Trained Korean-English cross-lingual retrieval embedding model and analyzed language-pair trade-offs; used model merging to recover mono-lingual retrieval while retaining CLIR gains. [[Paper](https://arxiv.org/abs/2507.08480)]
