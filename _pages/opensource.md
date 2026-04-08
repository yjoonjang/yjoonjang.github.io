---
layout: page
title: Open Source
permalink: /opensource/
description: Contributions to major NLP open-source projects.
nav: false
---

## [Sentence-Transformers](https://github.com/UKPLab/sentence-transformers) (2025-2026)

- Extended the cross-encoder training stack with classic learning-to-rank losses (Position-Aware ListMLELoss, RankNetLoss) and runnable examples. [[PR#6](https://github.com/tomaarsen/sentence-transformers/pull/6)] [[PR#7](https://github.com/tomaarsen/sentence-transformers/pull/7)]
- Introduced hardness-weighted contrastive learning to up-weight informative hard negatives across multiple losses via configurable hardness parameters. [[PR#3667](https://github.com/huggingface/sentence-transformers/pull/3667)]
- Implemented CachedSpladeLoss for gradient-cache compatible, memory-efficient SPLADE training, enabling 4-16x larger effective batch sizes with 36-41% lower GPU memory. [[PR#3670](https://github.com/huggingface/sentence-transformers/pull/3670)]

---

## [MTEB - Massive Text Embeddings Benchmark](https://github.com/embeddings-benchmark/mteb) (2024-2025)

- Added a Korean retrieval benchmark task (AutoRAGRetrieval) and polished task metadata, registration to expand multilingual retrieval coverage. [[PR#1388](https://github.com/embeddings-benchmark/mteb/pull/1388)]
- Improved stability of the OpenAI embedding wrapper by adding sentence trimming and tightening dependency handling. [[PR#1526](https://github.com/embeddings-benchmark/mteb/pull/1526)]
- Fixed NaN embeddings for Jasper models by switching from float16 to bfloat16, improving robustness of model evaluation. [[PR#2481](https://github.com/embeddings-benchmark/mteb/pull/2481)]

---

## [FlagEmbedding](https://github.com/FlagOpen/FlagEmbedding)

- Fixed a bug related to knowledge distillation when training. [[Issue#1170](https://github.com/FlagOpen/FlagEmbedding/issues/1170)]
