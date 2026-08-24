---
layout: page
title: ReviewSearch
description: Search engine over 205,988 real peer reviews and their author rebuttals.
importance: 3.5
category: research
github: https://github.com/yjoonjang/rebuttal-skills
---

Built a search engine over **205,988 real peer reviews and their author rebuttals** collected from ICLR, ICML, NeurIPS, and COLM, so authors can look up how a given reviewer concern was actually answered.

- Trained a hybrid retriever for the domain: a fine-tuned dense encoder and a sparse encoder fused with Reciprocal Rank Fusion
- Shipped it as the grounding layer for `RebuttalDraft` in the `rebuttal-skills` agent plugin, which drafts per-reviewer rebuttals and runs the supporting experiments in the author's own repository

[Blog](https://medium.com/@yjoonjang/introducing-rebuttal-skills-reviewsearch-rebuttaldraft-3fec218b78e9) | [GitHub](https://github.com/yjoonjang/rebuttal-skills) | [Demo](https://yjoonjang-reviewsearch.hf.space/)
