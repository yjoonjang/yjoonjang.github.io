# Resume → Website Sync Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Sync the al-folio Jekyll site to the updated `resume.tex`: restructure Publications into Conference/Domestic/Preprint, add 3 missing preprints, unify Hugging Face downloads to `1.3M+`, and rework the CV page.

**Architecture:** Static content edits only (Markdown, BibTeX, YAML). No theme/layout changes. Publications grouped via jekyll-scholar `--query @*[category=…]*` filters (confirmed supported by this al-folio version in `_includes/selected_papers.liquid`). CV page is driven by `_data/cv.yml` (`cv_format: rendercv`). Additive: demo content, `FlagEmbedding`, and `resume.tex` are preserved.

**Tech Stack:** Jekyll, jekyll-scholar (BibTeX), al-folio rendercv, Docker Compose (preview/verify), Prettier.

**Branch:** `resume-website-sync` (already created; spec committed at `docs/superpowers/specs/2026-05-16-resume-website-sync-design.md`).

**Verification model:** This is a static site with no unit-test framework. Per-task verification = deterministic static checks (`grep`, file content). The integration gate is **Task 9** (Docker build + visual + grep), which also runs Prettier. `resume.tex` and `.omc/` stay untracked throughout.

---

### Task 1: Restructure `_bibliography/papers.bib`

Add a `category` field to every entry, add 3 new preprint entries, fix two `html` links to match `resume.tex`, and order entries so each category lists in resume order (page uses `--group_by none`, which preserves file order).

**Files:**

- Modify (full overwrite): `_bibliography/papers.bib`

- [ ] **Step 1: Overwrite `_bibliography/papers.bib` with the exact content below**

```bibtex
---
---

@inproceedings{jang2026sigir,
  abbr        = {SIGIR 2026},
  bibtex_show = {true},
  title       = {Beyond Hard Negatives: The Importance of Score Distribution in Knowledge Distillation for Dense Retrieval},
  author      = {Jang, Youngjoon and Hong, Seongtae and Moon, Hyeonseok and Lim, Heuiseok},
  year        = {2026},
  booktitle   = {Proceedings of the 49th International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR 2026)},
  html        = {https://arxiv.org/abs/2604.04734},
  arxiv       = {2604.04734},
  category    = {conference},
  selected    = {true},
  preview     = {sigir2026.png},
  abstract    = {Investigating the importance of score distribution in knowledge distillation for dense retrieval, going beyond hard negatives.}
}

@inproceedings{hong2026iclr,
  abbr        = {ICLR 2026},
  bibtex_show = {true},
  title       = {Improving Semantic Proximity in Information Retrieval through Cross-Lingual Alignment},
  author      = {Hong, Seongtae and Jang, Youngjoon and Lee, Jungseob and Moon, Hyeonseok and Lim, Heuiseok},
  year        = {2026},
  booktitle   = {Proceedings of the International Conference on Learning Representations (ICLR 2026)},
  html        = {https://openreview.net/forum?id=NvKvW5k6Kk},
  category    = {conference},
  selected    = {true},
  preview     = {iclr2026.png},
  abstract    = {Improving semantic proximity in information retrieval through cross-lingual alignment techniques.}
}

@inproceedings{jang2026legalmidm,
  abbr        = {ICLR WS 2026},
  bibtex_show = {true},
  title       = {LEGALMIDM: Use-Case-Driven Legal Domain Specialization for Korean Large Language Model},
  author      = {Jang, Youngjoon and Park, Chanhee and Moon, Hyeonseok and Ham, Young-kyoung and Moon, Jiwon and Kim, Jinhyeon and Jung, JuKyung and Lim, Heuiseok},
  year        = {2026},
  booktitle   = {ICLR 2026 Data-FM Workshop},
  html        = {https://arxiv.org/abs/2604.25297},
  category    = {conference},
  selected    = {true},
  preview     = {legalmidm.png},
  abstract    = {Use-case-driven legal domain specialization for Korean Large Language Model.}
}

@inproceedings{lee2026clear,
  abbr        = {ACL 2026},
  bibtex_show = {true},
  title       = {CLEAR: Cross-Lingual Enhancement in Retrieval via Reverse-training},
  author      = {Lee, Seungyoon and Kim, Minhyuk and Hong, Seongtae and Jang, Youngjoon and Oh, Dongsuk and Lim, Heuiseok},
  year        = {2026},
  booktitle   = {Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics (ACL 2026)},
  html        = {https://arxiv.org/abs/2604.05821},
  category    = {conference},
  selected    = {true},
  preview     = {clear2026.png},
  abstract    = {Cross-lingual enhancement in retrieval via reverse-training.}
}

@inproceedings{jang2025coreference,
  abbr        = {ACL SRW 2025},
  bibtex_show = {true},
  title       = {From Ambiguity to Accuracy: The Transformative Effect of Coreference Resolution on Retrieval-Augmented Generation systems},
  author      = {Jang, Youngjoon and Hong, Seongtae and Son, Junyoung and Park, Sungjin and Park, Chanjun and Lim, Heuiseok},
  year        = {2025},
  booktitle   = {Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics: Student Research Workshop (ACL 2025 SRW)},
  html        = {https://aclanthology.org/2025.acl-srw.27/},
  category    = {conference},
  selected    = {true},
  preview     = {coreference_rag.png},
  abstract    = {Investigating how coreference resolution improves the accuracy of Retrieval-Augmented Generation systems.}
}

@inproceedings{koo2024whereami,
  abbr        = {EMNLP 2024},
  bibtex_show = {true},
  title       = {Where am I? Large Language Models Wandering between Semantics and Structures in Long Contexts},
  author      = {Koo, Seonmin and Kim, Jinsung and Jang, Youngjoon and Park, Chanjun and Lim, Heuiseok},
  year        = {2024},
  booktitle   = {Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing (EMNLP 2024)},
  html        = {https://aclanthology.org/2024.emnlp-main.783/},
  category    = {conference},
  selected    = {true},
  preview     = {whereami_llm.png},
  abstract    = {Exploring how Large Language Models navigate between semantics and structures in long context scenarios.}
}

@inproceedings{jang2025kure,
  abbr        = {HCLT 2025},
  bibtex_show = {true},
  title       = {KURE: Embedding Model for Korean-Specific Retrieval},
  author      = {Jang, Youngjoon and Son, Junyoung and Lee, Taemin and Hong, Seongtae and Park, Jungbae and Lim, Heuiseok},
  year        = {2025},
  booktitle   = {Annual Conference on Human \& Cognitive Language Technology (HCLT 2025)},
  html        = {https://www.koreascience.kr/article/CFKO202533761230731.pdf},
  award       = {Best Oral Presentation Award},
  award_name  = {Best Paper},
  category    = {domestic},
  selected    = {true},
  preview     = {kure.png},
  abstract    = {Embedding model for Korean-specific retrieval achieving state-of-the-art performance.}
}

@inproceedings{jang2024koe5,
  abbr        = {HCLT 2024},
  bibtex_show = {true},
  title       = {KoE5: A New Dataset and Model for Improving Korean Embedding Performance},
  author      = {Jang, Youngjoon and Son, Junyoung and Lee, Taemin and Hong, Seongtae and Park, Jungbae and Lim, Heuiseok},
  year        = {2024},
  booktitle   = {Annual Conference on Human \& Cognitive Language Technology (HCLT 2024)},
  html        = {https://koreascience.kr/article/CFKO202404272001146.page},
  category    = {domestic},
  selected    = {false},
  preview     = {koe5.png},
  abstract    = {Introducing KoE5, a new dataset and model specifically designed to improve Korean text embedding performance.}
}

@article{jang2026mlaire,
  abbr        = {Preprint},
  bibtex_show = {true},
  title       = {MLAIRE: Multilingual Language-Aware Information Retrieval Evaluation Protocol},
  author      = {Jang, Youngjoon and Hong, Seongtae and Moon, Hyeonseok and Lim, Heuiseok},
  year        = {2026},
  journal     = {Under Review},
  html        = {https://arxiv.org/abs/2605.07249},
  arxiv       = {2605.07249},
  category    = {preprint},
  selected    = {false},
  abstract    = {A multilingual, language-aware evaluation protocol for information retrieval.}
}

@article{jang2026mimo,
  abbr        = {Preprint},
  bibtex_show = {true},
  title       = {MIMO: Multilingual Information Retrieval from Monolingual Oracles},
  author      = {Jang, Youngjoon and Hong, Seongtae and Lim, Heuiseok},
  year        = {2026},
  journal     = {Under Review},
  category    = {preprint},
  selected    = {false},
  abstract    = {Multilingual information retrieval leveraging monolingual oracles.}
}

@article{jang2026shift,
  abbr        = {Preprint},
  bibtex_show = {true},
  title       = {SHIFT: Semantic Harmonization via Index-side Feature Transformation for Multilingual Information Retrieval},
  author      = {Jang, Youngjoon and Hong, Seongtae and Moon, Hyeonseok and Lim, Heuiseok},
  year        = {2026},
  journal     = {Under Review},
  category    = {preprint},
  selected    = {false},
  abstract    = {Semantic harmonization via index-side feature transformation for multilingual information retrieval.}
}

@article{jang2025crosslingual,
  abbr        = {ArXiv 2025},
  bibtex_show = {true},
  title       = {Improving Korean-English Cross-Lingual Retrieval: A Data-Centric Study of Language Composition and Model Merging},
  author      = {Jang, Youngjoon and Son, Junyoung and Lee, Taemin and Hong, Seongtae and Moon, Hyeonseok and Lee, Seungyoon and Matteson, Andrew and Lim, Heuiseok},
  year        = {2025},
  journal     = {ArXiv Preprint},
  html        = {https://arxiv.org/abs/2507.08480},
  arxiv       = {2507.08480},
  category    = {preprint},
  selected    = {true},
  preview     = {crosslingual_retrieval.png},
  abstract    = {A data-centric study on improving Korean-English cross-lingual retrieval through language composition and model merging techniques.}
}

@article{ncai2025vaetki,
  abbr        = {ArXiv 2025},
  bibtex_show = {true},
  title       = {VAETKI Technical Report},
  author      = {{NC-AI Consortium}},
  year        = {2025},
  journal     = {ArXiv Preprint},
  html        = {https://github.com/wbl-ncai/VAETKI/blob/releases/v1.0.0/VAETKI_Technical_Report.pdf},
  category    = {preprint},
  preview     = {vaetki.png},
  abstract    = {Technical report for the VAETKI project by the NC-AI Consortium.}
}
```

- [ ] **Step 2: Verify structure with grep**

Run:

```bash
grep -c "category    = {conference}" _bibliography/papers.bib
grep -c "category    = {domestic}" _bibliography/papers.bib
grep -c "category    = {preprint}" _bibliography/papers.bib
grep -c "^@" _bibliography/papers.bib
grep -n "openreview.net/forum?id=NvKvW5k6Kk\|arxiv.org/abs/2604.25297" _bibliography/papers.bib
```

Expected: conference `6`, domestic `2`, preprint `5`, total `@` entries `13`, and both fixed links present (ICLR → openreview NvKvW5k6Kk, LEGALMIDM → arxiv 2604.25297).

- [ ] **Step 3: Commit**

```bash
git add _bibliography/papers.bib
git commit -m "feat(bib): categorize publications + add MLAIRE/MIMO/SHIFT preprints"
```

---

### Task 2: Rebuild Publications page into 3 sections + filter `category` keyword

**Files:**

- Modify (full overwrite): `_pages/publications.md`
- Modify: `_config.yml` (add `category` to `filtered_bibtex_keywords`)

- [ ] **Step 1: Overwrite `_pages/publications.md` with exactly this content**

Headings are explicit `<h2>` (kramdown does not parse `##` inside a block-level `<div>`; Liquid tags are processed regardless):

```markdown
---
layout: page
permalink: /publications/
title: Publications
description: Publications grouped by category, mirroring the resume. Generated by jekyll-scholar.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<div class="publications">

<h2>Publications [Conference]</h2>

{% bibliography --query @*[category=conference]* --group_by none %}

<h2>Publications [Domestic Conference]</h2>

{% bibliography --query @*[category=domestic]* --group_by none %}

<h2>Preprint</h2>

{% bibliography --query @*[category=preprint]* --group_by none %}

</div>
```

- [ ] **Step 2: Add `category` to `filtered_bibtex_keywords` in `_config.yml`**

Find this exact block fragment in `_config.yml`:

```yaml
bibtex_show,
blog,
code,
```

Replace it with:

```yaml
bibtex_show,
blog,
category,
code,
```

- [ ] **Step 3: Verify**

Run:

```bash
grep -c "{% bibliography --query @\*\[category=" _pages/publications.md
grep -n "category," _config.yml
```

Expected: publications.md shows `3`; `_config.yml` shows the `category,` line inside the keyword list.

- [ ] **Step 4: Commit**

```bash
git add _pages/publications.md _config.yml
git commit -m "feat(publications): split into Conference/Domestic/Preprint sections"
```

---

### Task 3: Update `_pages/about.md` research summary

**Files:**

- Modify: `_pages/about.md`

- [ ] **Step 1: Replace the research paragraph**

Find this exact line:

```
My research focuses on **Information Retrieval (IR)** and **Retrieval-Augmented Generation (RAG)** systems. I aim to make AI models more beneficial to humans and society.
```

Replace with:

```
My research centers on **information retrieval** — dense, sparse, and late-interaction retrieval — along with **multilingual information retrieval** and **retrieval-augmented generation (RAG)**. My work has been published at top-tier AI and IR venues including **SIGIR, ICLR, ACL, and EMNLP**. I have contributed retrieval training losses and evaluation utilities to open-source ecosystems such as Sentence-Transformers and MTEB, and led Korean retrieval model and benchmark projects that achieved **200+ GitHub stars and 1.3M+ cumulative Hugging Face downloads**. I aim to make AI models more beneficial to humans and society.
```

- [ ] **Step 2: Verify**

Run:

```bash
grep -c "1.3M+ cumulative Hugging Face downloads" _pages/about.md
grep -c "SIGIR, ICLR, ACL, and EMNLP" _pages/about.md
```

Expected: each `1`.

- [ ] **Step 3: Commit**

```bash
git add _pages/about.md
git commit -m "feat(about): align research summary with updated resume"
```

---

### Task 4: Update `_pages/opensource.md` (EmbedDistillLoss + InstructKR)

**Files:**

- Modify: `_pages/opensource.md`

- [ ] **Step 1: Add the EmbedDistillLoss bullet (resume order: after the learning-to-rank bullet)**

Find this exact two-line fragment:

```
- Extended the cross-encoder training stack with classic learning-to-rank losses (Position-Aware ListMLELoss, RankNetLoss) and runnable examples. [[PR#6](https://github.com/tomaarsen/sentence-transformers/pull/6)] [[PR#7](https://github.com/tomaarsen/sentence-transformers/pull/7)]
- Introduced hardness-weighted contrastive learning to up-weight informative hard negatives across multiple losses via configurable hardness parameters. [[PR#3667](https://github.com/huggingface/sentence-transformers/pull/3667)]
```

Replace with:

```
- Extended the cross-encoder training stack with classic learning-to-rank losses (Position-Aware ListMLELoss, RankNetLoss) and runnable examples. [[PR#6](https://github.com/tomaarsen/sentence-transformers/pull/6)] [[PR#7](https://github.com/tomaarsen/sentence-transformers/pull/7)]
- Implemented `EmbedDistillLoss` to support direct embedding-level knowledge distillation, enabling efficient representation transfer from teacher to student models. [[PR#3665](https://github.com/huggingface/sentence-transformers/pull/3665)]
- Introduced hardness-weighted contrastive learning to up-weight informative hard negatives across multiple losses via configurable hardness parameters. [[PR#3667](https://github.com/huggingface/sentence-transformers/pull/3667)]
```

- [ ] **Step 2: Add the InstructKR section before the FlagEmbedding section**

Find this exact fragment:

```
---

## [FlagEmbedding](https://github.com/FlagOpen/FlagEmbedding)
```

Replace with:

```
---

## [InstructKR](https://github.com/instructkr) (2026)

- Led the Korean Reranker evaluation and leaderboard project, establishing a standardized Korean benchmark suite for text reranking models. [[GitHub](https://github.com/instructkr/reranker-simple-benchmark)]

---

## [FlagEmbedding](https://github.com/FlagOpen/FlagEmbedding)
```

- [ ] **Step 3: Verify**

Run:

```bash
grep -c "EmbedDistillLoss" _pages/opensource.md
grep -c "reranker-simple-benchmark" _pages/opensource.md
grep -c "FlagEmbedding" _pages/opensource.md
```

Expected: `EmbedDistillLoss` `1`, `reranker-simple-benchmark` `1`, `FlagEmbedding` ≥`2` (section heading + link still present).

- [ ] **Step 4: Commit**

```bash
git add _pages/opensource.md
git commit -m "feat(opensource): add EmbedDistillLoss PR and InstructKR section"
```

---

### Task 5: Unify Hugging Face downloads to `1.3M+`

**Files:**

- Modify: `_pages/projects.md`
- Modify: `_projects/kure.md`

- [ ] **Step 1: `_pages/projects.md` — update KURE downloads**

Find this exact line:

```
- Open-sourced the framework, achieving **200+ GitHub stars and 1.1M+ cumulative downloads** on Hugging Face.
```

Replace with:

```
- Open-sourced the framework, achieving **200+ GitHub stars and 1.3M+ cumulative downloads** on Hugging Face.
```

- [ ] **Step 2: `_pages/projects.md` — add WBL Hugging Face link (matches existing heading style)**

Find this exact line:

```
## WBL: World Best LLM Project
```

Replace with:

```
## WBL: World Best LLM Project &nbsp; [HuggingFace](https://huggingface.co/NC-AI-consortium-VAETKI/VAETKI)
```

- [ ] **Step 3: `_projects/kure.md` — update KURE downloads**

Find this exact line:

```
- Open-sourced the framework, achieving **200+ GitHub stars and 1.1M+ cumulative downloads** on Hugging Face
```

Replace with:

```
- Open-sourced the framework, achieving **200+ GitHub stars and 1.3M+ cumulative downloads** on Hugging Face
```

- [ ] **Step 4: Verify no stale figures remain site-wide**

Run:

```bash
grep -rn "1\.1M\|1\.2M" _pages/ _projects/ _data/ _bibliography/ _news/ 2>/dev/null || echo "CLEAN"
grep -rc "1.3M+" _pages/projects.md _projects/kure.md
```

Expected: first command prints `CLEAN` (no `1.1M`/`1.2M` anywhere in content dirs); second shows `1` for each file.

- [ ] **Step 5: Commit**

```bash
git add _pages/projects.md _projects/kure.md
git commit -m "fix: unify Hugging Face downloads to 1.3M+ and add WBL HF link"
```

---

### Task 6: Rework `_data/cv.yml`

Reuse only rendercv entry shapes already proven to render in the current file: Education-style (`institution`/`area`/`start_date`/`end_date`/`highlights`) for Open Source & Projects, Awards-style (`title`/`authors`/`date`/`awarder`/`summary`) for Publications & Awards, plus the existing Skills and Languages shapes.

**Files:**

- Modify (full overwrite): `_data/cv.yml`

- [ ] **Step 1: Overwrite `_data/cv.yml` with exactly this content**

```yaml
cv:
  name: Youngjoon Jang
  label: Retrieval Researcher & Engineer
  email: yjoonjang34@gmail.com
  location: Seoul, South Korea
  image: ""
  summary: >-
    Retrieval researcher and engineer specializing in dense, sparse, and
    late-interaction retrieval, multilingual information retrieval, and
    retrieval-augmented generation. Published at SIGIR, ICLR, ACL, and EMNLP;
    led Korean retrieval models and benchmarks with 200+ GitHub stars and
    1.3M+ cumulative Hugging Face downloads.

  social_networks:
    - network: GitHub
      username: yjoonjang
    - network: LinkedIn
      username: yjoonjang

  sections:
    Education:
      - institution: Korea University
        location: Seoul, South Korea
        url: https://www.korea.edu/
        area: Computer Science and Engineering
        studyType: M.S.
        start_date: 2025
        end_date: Present
        highlights:
          - "NLP&AI Lab, advised by Prof. Heuiseok Lim"
          - "Research focus: Information Retrieval, Multilingual IR, RAG"

      - institution: Hongik University
        location: Seoul, South Korea
        area: Computer Engineering & Mechanical and System Design Engineering (Double Major)
        studyType: B.S.
        start_date: 2020
        end_date: 2025

    Publications [Conference]:
      - title: "Beyond Hard Negatives: The Importance of Score Distribution in Knowledge Distillation for Dense Retrieval"
        authors:
          - "Youngjoon Jang, Seongtae Hong, Hyeonseok Moon, Heuiseok Lim"
        date: 2026
        awarder: "SIGIR 2026"
      - title: "Improving Semantic Proximity in Information Retrieval through Cross-Lingual Alignment"
        authors:
          - "Seongtae Hong, Youngjoon Jang, Jungseob Lee, Hyeonseok Moon, Heuiseok Lim"
        date: 2026
        awarder: "ICLR 2026"
      - title: "LEGALMIDM: Use-Case-Driven Legal Domain Specialization for Korean Large Language Model"
        authors:
          - "Youngjoon Jang, Chanhee Park, Hyeonseok Moon, Young-kyoung Ham, Jiwon Moon, Jinhyeon Kim, JuKyung Jung, Heuiseok Lim"
        date: 2026
        awarder: "ICLR 2026 Data-FM Workshop"
      - title: "CLEAR: Cross-Lingual Enhancement in Retrieval via Reverse-training"
        authors:
          - "Seungyoon Lee, Minhyuk Kim, Seongtae Hong, Youngjoon Jang, Dongsuk Oh, Heuiseok Lim"
        date: 2026
        awarder: "ACL 2026"
      - title: "From Ambiguity to Accuracy: The Transformative Effect of Coreference Resolution on Retrieval-Augmented Generation systems"
        authors:
          - "Youngjoon Jang, Seongtae Hong, Junyoung Son, Sungjin Park, Chanjun Park, Heuiseok Lim"
        date: 2025
        awarder: "ACL 2025 SRW"
      - title: "Where am I? Large Language Models Wandering between Semantics and Structures in Long Contexts"
        authors:
          - "Seonmin Koo, Jinsung Kim, Youngjoon Jang, Chanjun Park, Heuiseok Lim"
        date: 2024
        awarder: "EMNLP 2024"

    Publications [Domestic Conference]:
      - title: "KURE: Embedding Model for Korean-Specific Retrieval"
        authors:
          - "Youngjoon Jang, Junyoung Son, Taemin Lee, Seongtae Hong, Jungbae Park, Heuiseok Lim"
        date: 2025
        awarder: "HCLT 2025"
        summary: "Best Oral Presentation Award"
      - title: "KoE5: A New Dataset and Model for Improving Korean Embedding Performance"
        authors:
          - "Youngjoon Jang, Junyoung Son, Taemin Lee, Seongtae Hong, Jungbae Park, Heuiseok Lim"
        date: 2024
        awarder: "HCLT 2024"

    Preprint:
      - title: "MLAIRE: Multilingual Language-Aware Information Retrieval Evaluation Protocol"
        authors:
          - "Youngjoon Jang, Seongtae Hong, Hyeonseok Moon, Heuiseok Lim"
        date: 2026
        awarder: "Under Review"
      - title: "MIMO: Multilingual Information Retrieval from Monolingual Oracles"
        authors:
          - "Youngjoon Jang, Seongtae Hong, Heuiseok Lim"
        date: 2026
        awarder: "Under Review"
      - title: "SHIFT: Semantic Harmonization via Index-side Feature Transformation for Multilingual Information Retrieval"
        authors:
          - "Youngjoon Jang, Seongtae Hong, Hyeonseok Moon, Heuiseok Lim"
        date: 2026
        awarder: "Under Review"
      - title: "Improving Korean-English Cross-Lingual Retrieval: A Data-Centric Study of Language Composition and Model Merging"
        authors:
          - "Youngjoon Jang, Junyoung Son, Taemin Lee, Seongtae Hong, Hyeonseok Moon, Seungyoon Lee, Andrew Matteson, Heuiseok Lim"
        date: 2025
        awarder: "arXiv"
      - title: "VAETKI Technical Report"
        authors:
          - "NC-AI Consortium"
        date: 2025
        awarder: "arXiv"

    Open Source Contributions:
      - institution: "Sentence-Transformers"
        area: "Open Source"
        start_date: 2025
        end_date: 2026
        highlights:
          - "Extended the cross-encoder training stack with classic learning-to-rank losses (RankNetLoss, ListMLELoss, Position-Aware ListMLELoss) and runnable examples."
          - "Implemented EmbedDistillLoss for direct embedding-level knowledge distillation (PR #3665)."
          - "Introduced hardness-weighted contrastive learning to up-weight informative hard negatives (PR #3667)."
          - "Implemented CachedSpladeLoss for gradient-cache compatible, memory-efficient SPLADE training (PR #3670)."
      - institution: "MTEB (Massive Text Embeddings Benchmark)"
        area: "Open Source"
        start_date: 2024
        end_date: 2025
        highlights:
          - "Added a Korean retrieval benchmark task (AutoRAGRetrieval) and polished task metadata and registration (PR #1388)."
          - "Improved stability of the OpenAI embedding wrapper with sentence trimming and tighter dependency handling (PR #1526)."
          - "Fixed NaN embeddings for Jasper models by switching from float16 to bfloat16 (PR #2481)."
      - institution: "InstructKR"
        area: "Open Source"
        start_date: 2026
        end_date: 2026
        highlights:
          - "Led the Korean Reranker evaluation and leaderboard project, establishing a standardized Korean benchmark suite for text reranking models."

    Projects:
      - institution: "WBL: World Best LLM Project"
        area: "Research"
        start_date: 2025
        end_date: 2025
        highlights:
          - "Led the data team; built a query clarity evaluation framework with engineered GPT-5.2 prompts and a Qwen3-4B tagger."
          - "Established a response filtering pipeline ensembling three reward models with score fusion."
          - "Curated large-scale alignment samples using LLM-as-a-judge and code-execution metrics."
      - institution: "KURE: Korea University Retrieval Embedding Model"
        area: "Research"
        highlights:
          - "Led the lab's flagship Korean retrieval project; trained a SOTA dense retriever (1st on MTEB-ko-retrieval, Aug. 2025)."
          - "Designed and maintained MTEB-ko-retrieval, a standardized public Korean IR leaderboard."
          - "Open-sourced the framework: 200+ GitHub stars and 1.3M+ cumulative Hugging Face downloads (Best Oral, HCLT 2025)."
      - institution: "Korean ColBERT & Sparse Retrievers"
        area: "Research"
        highlights:
          - "Trained and open-sourced Korean ColBERT and SPLADE variants achieving SOTA among corresponding architectures (Feb. 2026)."
          - "Provided optimized, reproducible pipelines advancing dense-sparse hybrid retrieval experiments."
      - institution: "KT–Korea University Collaborative Research (Korean Legal LLM)"
        area: "Research"
        highlights:
          - "Developed an end-to-end training recipe for a Korean legal-domain LLM with expert-written and synthetic alignment data."
          - "Directly contributed to KT winning a $10.42M contract to build an AI platform for the South Korean Supreme Court."
          - "Published the methodology as LEGALMIDM at the ICLR 2026 Data-FM Workshop."
      - institution: "PreRanker"
        area: "Research"
        highlights:
          - "Built a lightweight reranker to narrow candidate tools, reducing tool-call scope for LLM agents."
      - institution: "URACLE–Korea University Collaborative Research"
        area: "Research"
        highlights:
          - "Trained a Korean–English cross-lingual retrieval model; used model merging to recover mono-lingual retrieval while retaining CLIR gains."

    Technical Skills:
      - name: "Languages"
        icon: fa-solid fa-code
        keywords: "Python, Bash, SQL"
      - name: "Machine Learning"
        icon: fa-solid fa-brain
        keywords: "PyTorch, Hugging Face (Transformers, Sentence-Transformers, Accelerate), vLLM"
      - name: "Infrastructure & Tools"
        icon: fa-solid fa-cloud
        keywords: "Docker, Linux, Git, Weights & Biases"

    Awards:
      - title: Best Oral Presentation Award
        authors:
          - "HCLT 2025"
        date: 2025
        awarder: Annual Conference on Human & Cognitive Language Technology
        summary: "Awarded for the paper: KURE: Embedding Model for Korean-Specific Retrieval"

    Languages:
      - name: Korean
        summary: "Native speaker"
      - name: English
        summary: "Fluent"
```

- [ ] **Step 2: Validate YAML syntax**

Run:

```bash
ruby -ryaml -e "YAML.load_file('_data/cv.yml'); puts 'YAML OK'"
```

Expected: `YAML OK`. (If `ruby` is unavailable, use: `python3 -c "import yaml,sys; yaml.safe_load(open('_data/cv.yml')); print('YAML OK')"` — install pyyaml if needed, or defer this check to the Docker build in Task 9.)

- [ ] **Step 3: Verify content**

Run:

```bash
grep -c "Publications \[Conference\]:\|Publications \[Domestic Conference\]:\|Preprint:" _data/cv.yml
grep -c "Django\|FastAPI\|Next.js\|AWS" _data/cv.yml
grep -c "1.3M+ cumulative Hugging Face downloads" _data/cv.yml
```

Expected: section headers `3`; stale skills (`Django/FastAPI/Next.js/AWS`) `0`; KURE downloads line `1`.

- [ ] **Step 4: Commit**

```bash
git add _data/cv.yml
git commit -m "feat(cv): rework cv.yml from resume (skills, publications, projects)"
```

---

### Task 7: Update `_pages/cv.md` (remove demo PDF, expose in nav)

**Files:**

- Modify: `_pages/cv.md`

- [ ] **Step 1: Overwrite `_pages/cv.md` with exactly this content**

```markdown
---
layout: cv
permalink: /cv/
title: CV
nav: true
nav_order: 5
cv_format: rendercv # options: rendercv, jsonresume
description: Curriculum Vitae of Youngjoon Jang — research, publications, open-source contributions, and projects in information retrieval and RAG.
toc:
  sidebar: left
---
```

- [ ] **Step 2: Verify**

Run:

```bash
grep -c "cv_pdf" _pages/cv.md
grep -c "nav: true" _pages/cv.md
grep -c "example_pdf" _pages/cv.md
```

Expected: `cv_pdf` `0`, `nav: true` `1`, `example_pdf` `0`.

- [ ] **Step 3: Commit**

```bash
git add _pages/cv.md
git commit -m "feat(cv): remove demo PDF button, expose CV in navbar"
```

---

### Task 8: Add news items (additive)

Keep existing `_news/news_1.md` (SIGIR 2026) and `_news/news_2.md` (LEGALMIDM). Add three new inline news posts. Filenames continue the `news_N.md` sequence.

**Files:**

- Create: `_news/news_3.md`
- Create: `_news/news_4.md`
- Create: `_news/news_5.md`

- [ ] **Step 1: Create `_news/news_3.md`**

```markdown
---
layout: post
date: 2026-03-03 00:00:00+0900
inline: true
related_posts: false
---

Paper accepted at **ICLR 2026**: "Improving Semantic Proximity in Information Retrieval through Cross-Lingual Alignment"
```

- [ ] **Step 2: Create `_news/news_4.md`**

```markdown
---
layout: post
date: 2026-01-23 00:00:00+0900
inline: true
related_posts: false
---

Paper accepted at **ACL 2026**: "CLEAR: Cross-Lingual Enhancement in Retrieval via Reverse-training"
```

- [ ] **Step 3: Create `_news/news_5.md`**

```markdown
---
layout: post
date: 2025-10-17 00:00:00+0900
inline: true
related_posts: false
---

Received the **Best Oral Presentation Award** at **HCLT 2025** for "KURE: Embedding Model for Korean-Specific Retrieval"
```

- [ ] **Step 4: Verify**

Run:

```bash
ls _news/news_*.md | wc -l
grep -l "ICLR 2026\|ACL 2026\|Best Oral Presentation Award" _news/news_3.md _news/news_4.md _news/news_5.md
```

Expected: `5` news files; all three new files matched.

- [ ] **Step 5: Commit**

```bash
git add _news/news_3.md _news/news_4.md _news/news_5.md
git commit -m "feat(news): add ICLR 2026, ACL 2026, and HCLT Best Oral items"
```

---

### Task 9: Docker build + comprehensive verification (integration gate)

This is the real verification gate. It builds the site, checks every acceptance criterion, applies Prettier, and fixes any rendering issues found.

**Files:**

- Potentially modify: `_pages/publications.md` (heading markup), `_data/cv.yml` (section entry shape) — only if Step 4 finds rendering defects.

- [ ] **Step 1: Start the Docker dev server (background)**

Run:

```bash
docker compose up --build
```

Run this in the background and wait for `Server running... press ctrl-c to stop.` Expected: build completes with **no Jekyll/jekyll-scholar errors** (watch for BibTeX parse errors or Liquid errors referencing `publications.md` / `cv.yml`).

- [ ] **Step 2: Smoke-check pages return HTTP 200**

Run:

```bash
for p in / /publications/ /cv/ /projects/ /opensource/; do printf "%s -> " "$p"; curl -s -o /dev/null -w "%{http_code}\n" "http://localhost:8080$p"; done
```

Expected: every path prints `200`.

- [ ] **Step 2b: Build artifact missing-figure check (non-blocking)**

The 3 new preprints intentionally have no `preview`. Confirm no other thumbnail broke:

```bash
grep -ro "category" _site/publications/index.html | head -1 && echo "category leaked into HTML (should be empty)" || echo "category not rendered (correct)"
```

Expected: `category not rendered (correct)` (the `category` field must be filtered out of visible output and the BibTeX popup).

- [ ] **Step 3: Verify Publications categorization in built HTML**

Run:

```bash
grep -o "Publications \[Conference\]\|Publications \[Domestic Conference\]\|Preprint" _site/publications/index.html | sort -u
grep -c "MLAIRE\|MIMO\|SHIFT" _site/publications/index.html
grep -c "bibliography" _site/publications/index.html
```

Expected: all three section titles present; new preprints (`MLAIRE/MIMO/SHIFT`) count ≥ `3`; at least one `bibliography` list rendered (bib-search intact).

- [ ] **Step 4: Visual verification (browse the running site)**

Open `http://localhost:8080` and visually confirm on `/`, `/publications/`, `/cv/`, `/projects/`, `/opensource/`:

- Publications page shows exactly three sections in order **Conference → Domestic → Preprint**, each paper in the correct category and in resume order; bib search box works; clicking "BibTeX" does NOT show a `category` field.
- CV page renders cleanly: reworked Technical Skills (Python/Bash/SQL, PyTorch/HF/vLLM, Docker/Linux/Git/W&B), the three Publications sections, Open Source, Projects, Awards, Languages; **no PDF icon** next to the title; CV link visible in the navbar; left TOC sidebar works.
- Dark-mode toggle works on every page; navbar correct.

**Remediation if defects found (apply, then re-verify Steps 3–4):**

- If the `<h2>` category headers render unstyled/misaligned: change them in `_pages/publications.md` to `<h2 class="bibliography">…</h2>`, or move each header out of the `<div class="publications">` wrapper into its own line above each `{% bibliography %}` call (keep the Liquid tags inside their own `<div class="publications">` wrappers).
- If any `_data/cv.yml` section renders as raw text / collapsed (rendercv didn't recognize the entry shape): convert that section's items to the Education-proven shape — each item becomes `- institution: "<title>"` with the descriptive text as a single-item `highlights:` list, and `area`/`start_date`/`end_date` as available. Example for a Publications entry:

  ```yaml
  - institution: "Beyond Hard Negatives: ... for Dense Retrieval"
    area: "SIGIR 2026"
    highlights:
      - "Youngjoon Jang, Seongtae Hong, Hyeonseok Moon, Heuiseok Lim"
  ```

  Apply uniformly within the affected section only.

- [ ] **Step 5: Site-wide stale-figure and link sanity grep**

Run:

```bash
grep -rn "1\.1M\|1\.2M" _pages/ _projects/ _data/ _bibliography/ _news/ 2>/dev/null || echo "DOWNLOADS CLEAN"
grep -rn "example_pdf" _pages/ 2>/dev/null || echo "PDF CLEAN"
git status --short
```

Expected: `DOWNLOADS CLEAN`, `PDF CLEAN`, and `git status` shows only `?? .omc/` and `?? resume.tex` untracked (no tracked changes lost; `_site/` is gitignored).

- [ ] **Step 6: Run Prettier (per AGENTS.md pre-commit checklist)**

Run:

```bash
npx prettier . --write
```

Then re-confirm the Docker site still builds without error (Jekyll auto-rebuilds on file change; check the running server log for errors). If Prettier reformats `_data/cv.yml`, `_bibliography/papers.bib`, or `publications.md`, re-run Step 3.

- [ ] **Step 7: Stop Docker and commit**

Run:

```bash
docker compose down
git add -A -- ':!resume.tex' ':!.omc'
git commit -m "chore: prettier formatting + verified resume sync build"
```

(If `git status` shows nothing to commit because Prettier made no changes and Steps were clean, skip the commit and note "no formatting changes needed".)

---

## Self-Review

**1. Spec coverage** (each spec §/requirement → task):

- §4.1 papers.bib category + 3 preprints + link fixes → **Task 1** ✓
- §4.1 publications.md 3 sections + `_config.yml` filtered keyword → **Task 2** ✓
- §4.2 about.md research summary + 1.3M+ → **Task 3** ✓
- §4.2 opensource.md EmbedDistillLoss + InstructKR (FlagEmbedding kept) → **Task 4** ✓
- §4.2 projects.md / kure.md 1.3M+ (+ WBL HF link) → **Task 5** ✓
- §4.3 cv.yml full rework (skills, pubs, open source, projects) → **Task 6** ✓
- §4.2 cv.md remove cv_pdf, nav:true, description → **Task 7** ✓
- §4.2 news additions (additive) → **Task 8** ✓
- §6 verification (Docker, 3-section order, CV render, no 1.1M/1.2M, links, dark mode, prettier) → **Task 9** ✓
- §3 non-goals (no theme change, demo/FlagEmbedding/resume.tex preserved) → enforced: no `_layouts`/`_sass` edits; FlagEmbedding kept (Task 4 Step 3 asserts it remains); Task 9 Step 5 asserts `resume.tex`/`.omc` stay untracked ✓
- §7 risk (rendercv shape, heading markup, missing preview) → Task 1 omits `preview` for new preprints; Task 9 Step 4 has concrete remediation ✓
- No gaps found.

**2. Placeholder scan:** No "TBD/TODO/implement later". Every code/content step contains the full literal content. The only conditional logic is Task 9 Step 4 remediation, which provides concrete, copy-pasteable alternatives (not placeholders).

**3. Type/name consistency:** BibTeX keys (`jang2026mlaire`, `jang2026mimo`, `jang2026shift`) are defined in Task 1 and referenced consistently in Task 9 Step 3 verification. `category` values (`conference`/`domestic`/`preprint`) match between Task 1 entries, Task 2 `--query` filters, and Task 2 `_config.yml` keyword. `1.3M+` figure is consistent across Tasks 3, 5, 6. cv.yml section names in Task 6 match the verification grep in Task 6 Step 3 and Task 9 Step 4.

Plan is internally consistent and fully covers the spec.
