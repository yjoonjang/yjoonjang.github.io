---
layout: page
title: Open-source Contributions
description: Major contributions to sentence-transformers, MTEB, and FlagEmbedding.
importance: 7
category: open-source
---

### Sentence-Transformers (2025-2026)
- Extended the cross-encoder training stack with classic learning-to-rank losses (Position-Aware ListMLELoss, RankNetLoss). [[PR#6](https://github.com/tomaarsen/sentence-transformers/pull/6)] [[PR#7](https://github.com/tomaarsen/sentence-transformers/pull/7)]
- Introduced hardness-weighted contrastive learning to up-weight informative hard negatives. [[PR#3667](https://github.com/huggingface/sentence-transformers/pull/3667)]
- Implemented CachedSpladeLoss for gradient-cache compatible, memory-efficient SPLADE training (4-16x larger batch sizes, 36-41% lower GPU memory). [[PR#3670](https://github.com/huggingface/sentence-transformers/pull/3670)]

### MTEB (2024-2025)
- Added Korean retrieval benchmark task (AutoRAGRetrieval). [[PR#1388](https://github.com/embeddings-benchmark/mteb/pull/1388)]
- Improved stability of OpenAI embedding wrapper with sentence trimming. [[PR#1526](https://github.com/embeddings-benchmark/mteb/pull/1526)]
- Fixed NaN embeddings for Jasper models (float16 → bfloat16). [[PR#2481](https://github.com/embeddings-benchmark/mteb/pull/2481)]
