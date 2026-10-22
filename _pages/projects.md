---
layout: page
title: Projects
permalink: /projects/
description: Research projects in NLP, Information Retrieval, and RAG.
nav: false
---

## WBL: World Best LLM Project &nbsp; [HuggingFace](https://huggingface.co/NC-AI-consortium-VAETKI/VAETKI)

- Led the data team and established a query clarity evaluation framework using engineered GPT-5.2 prompts, training a Qwen3-4B model as a proprietary tagger to selectively curate datasets with diverse clarity levels.
- Established a robust response filtering pipeline for off-policy SFT data by ensembling three distinct reward models, applying score fusion techniques to accurately evaluate and retain high-quality responses.
- Curated and refined large-scale alignment samples by integrating the score fusion pipeline with rigorous LLM-as-a-judge and Code Execution metrics to effectively eliminate repetitive and low-quality responses.

---

## [KURE: Korea University Retrieval Models](https://github.com/nlpai-lab/KURE) &nbsp; [GitHub](https://github.com/nlpai-lab/KURE) \| [HF](https://huggingface.co/collections/nlpai-lab/kure) \| [API](https://kure.kullm.ai/)

- Led the lab's flagship Korean-English retrieval project, built the MTEB-Ko-Retrieval Leaderboard, and open-sourced the model family and training/evaluation code, reaching **250+ GitHub stars**.
- **Dense & Multi-Vector:** Developed KURE-v1, KURE-v2, and KURE-v3. KURE-v1 and KURE-v2 both ranked **1st on the leaderboard** (as of Aug. 2025 and Oct. 2026, respectively). KURE-v1 surpassed **3M downloads**, KURE-v2, a multi-vector model, outperforms 8B dense models while being 50× smaller, and KURE-v3 outperforms Qwen3-Embedding-8B while being 7× smaller and is served through a public API.
- **Sparse:** Developed KURE-Sparse-{base, nano}, achieving state-of-the-art Korean sparse retrieval performance overall and under 0.5B parameters, respectively. The base model also outperforms 8B dense models.
- **Reranker:** Developed KURE-Reranker-{base, nano}, achieving state-of-the-art Korean reranking performance under 4B and 1B parameters, respectively. The 149M nano delivers 19.5× the throughput of Qwen3-Reranker-4B with only a 1.5-point gap in nDCG@10.

---

## ReviewSearch &nbsp; [Blog](https://medium.com/@yjoonjang/introducing-rebuttal-skills-reviewsearch-rebuttaldraft-3fec218b78e9) \| [GitHub](https://github.com/yjoonjang/rebuttal-skills) \| [Demo](https://yjoonjang-reviewsearch.hf.space/)

- Built and deployed a search engine over **205,988 real peer reviews and rebuttals** for agents, so that a rebuttal draft is grounded in how authors actually answered the same concern.
- Trained a hybrid retriever for the domain: a fine-tuned dense encoder and a sparse encoder fused with Reciprocal Rank Fusion.
- Shipped it as the grounding layer for `RebuttalDraft` in the `rebuttal-skills` agent plugin.

---

## URACLE-Korea University Collaborative Research

- Trained a Korean-English cross-lingual retriever and analyzed language-pair trade-offs. Used model merging to recover mono-lingual retrieval while retaining CLIR gains. [[Paper](https://arxiv.org/abs/2507.08480)]

---

## KT-Korea University Collaborative Research (Korean Legal LLM)

- Developed an end-to-end training recipe for a Korean legal-domain LLM. Defined real-world judicial tasks, curated expert-written and synthetic alignment datasets, and optimized training strategies to preserve general capabilities.
- This research directly contributed to KT winning a **$10.42 million contract** to build an AI platform for the South Korean Supreme Court. [[News](https://www.koreatimes.co.kr/business/tech-science/20250721/judiciary-meets-ai-kt-to-build-ai-platform-for-court-system)]
- Published the training methodologies and data pipelines as **LEGALMIDM** at the ICLR 2026 Data-FM Workshop.

{% comment %} PreRanker — hidden for now

## [PreRanker](https://github.com/yjoonjang/PreRanker) &nbsp; [GitHub](https://github.com/yjoonjang/PreRanker) \| [HuggingFace](https://huggingface.co/yjoonjang/preranker-v1)

- Built a lightweight reranker to narrow down candidate tools, reducing tool-call scope for LLM agents.

{% endcomment %}
