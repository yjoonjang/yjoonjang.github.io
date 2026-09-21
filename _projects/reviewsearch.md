---
layout: page
title: ReviewSearch
description: Search engine over 205,988 real peer reviews and rebuttals.
importance: 3.5
category: research
github: https://github.com/yjoonjang/rebuttal-skills
---

Built and deployed a search engine over **205,988 real peer reviews and rebuttals** for agents, so that a rebuttal draft is grounded in how authors actually answered the same concern.

- Trained a hybrid retriever for the domain: a fine-tuned dense encoder and a sparse encoder fused with Reciprocal Rank Fusion
- Shipped it as the grounding layer for `RebuttalDraft` in the `rebuttal-skills` agent plugin

[Blog](https://medium.com/@yjoonjang/introducing-rebuttal-skills-reviewsearch-rebuttaldraft-3fec218b78e9) | [GitHub](https://github.com/yjoonjang/rebuttal-skills) | [Demo](https://yjoonjang-reviewsearch.hf.space/)
