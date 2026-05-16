# Resume → Website Sync (al-folio) — Design Spec

- **Date:** 2026-05-16
- **Owner:** Youngjoon Jang (yjoonjang)
- **Status:** Approved (design), pending implementation plan
- **Source of truth:** `/Users/jang-youngjoon/yjoonjang.github.io/resume.tex` (reference only — file itself is NOT modified, NOT committed; stays untracked)

## 1. Goal

Synchronize the existing al-folio Jekyll site so every fact matches the updated
`resume.tex`, restructure the Publications page into the resume's three
categories, and unify the Hugging Face download figure across the site.
No theme/layout changes. Demo content is preserved (additive approach).

## 2. Context

The site is **already substantially customized** (not a fresh setup). Existing
content matches an _older_ version of the resume. This is a **sync + additive**
task, not a from-scratch build.

Constraints / decisions confirmed with the user:

- Keep all leftover al-folio demo content (Einstein about, books/teaching pages,
  `repositories.yml` defaults). Do not delete.
- Keep `FlagEmbedding` open-source entry even though it is not in `resume.tex`
  (it is a real contribution). Approach is **additive**: add what's new, fix
  wrong facts, do not remove real content.
- Unify Hugging Face cumulative downloads to **`1.3M+`** everywhere
  (resume.tex is internally inconsistent: 1.3M in summary vs 1.2M in KURE;
  site currently says 1.1M).
- CV page content driven by `_data/cv.yml` (`cv_format: rendercv`).
- `resume.tex` is a read-only reference. No LaTeX compilation, no PDF.
  Remove the demo PDF download button.
- **New requirement:** Publications must be grouped into the resume's three
  categories: `Publications [Conference]`, `Publications [Domestic Conference]`,
  `Preprint`.
- Verify via Docker local preview (`docker compose up --build`,
  http://localhost:8080). Docker confirmed available (v29.3.1, compose v5.1.0).
- No system LaTeX toolchain present (xelatex/tectonic/pdflatex absent).

## 3. Non-Goals

- No theme, layout, CSS, or `_layouts`/`_includes` changes.
- No deletion of demo pages/data or `FlagEmbedding`.
- No LaTeX → PDF compilation; no CV PDF asset.
- No changes to `resume.tex` itself.
- No deployment (user deploys); scope ends at verified local build + prettier.

## 4. Design

### 4.1 Publications restructure (three categories)

**`_bibliography/papers.bib`**

- Add a custom `category` field to every entry, valued one of
  `conference` | `domestic` | `preprint`:
  - `conference`: `jang2026sigir` (SIGIR 2026), `hong2026iclr` (ICLR 2026),
    `jang2026legalmidm` (ICLR Data-FM Workshop 2026), `lee2026clear` (ACL 2026),
    `jang2025coreference` (ACL SRW 2025), `koo2024whereami` (EMNLP 2024)
  - `domestic`: `jang2025kure` (HCLT 2025, Best Oral), `jang2024koe5` (HCLT 2024)
  - `preprint`: new `MLAIRE`, new `MIMO`, new `SHIFT`,
    `jang2025crosslingual` (arXiv 2507.08480), `ncai2025vaetki` (VAETKI)
- Add 3 new `@article` entries (Under Review), with `category = {preprint}`:
  - **MLAIRE**: "MLAIRE: Multilingual Language-Aware Information Retrieval
    Evaluation Protocol", authors: Jang, Youngjoon and Hong, Seongtae and
    Moon, Hyeonseok and Lim, Heuiseok; `html = https://arxiv.org/abs/2605.07249`;
    note "Under Review".
  - **MIMO**: "MIMO: Multilingual Information Retrieval from Monolingual
    Oracles", authors: Jang, Youngjoon and Hong, Seongtae and Lim, Heuiseok;
    no link; note "Under Review".
  - **SHIFT**: "SHIFT: Semantic Harmonization via Index-side Feature
    Transformation for Multilingual Information Retrieval", authors: Jang,
    Youngjoon and Hong, Seongtae and Moon, Hyeonseok and Lim, Heuiseok;
    no link; note "Under Review".
  - New entries follow existing bib field conventions (`abbr`, `bibtex_show`,
    `year = {2026}`, `journal = {Under Review}`, `selected`, `abstract`).
    **Omit the `preview` field** for the 3 new preprints to avoid
    missing-thumbnail artifacts (consistent with §7).
- Align `html` links to `resume.tex` (resume = source of truth):
  - `hong2026iclr`: `https://arxiv.org/abs/2604.05684`
    → `https://openreview.net/forum?id=NvKvW5k6Kk`
  - `jang2026legalmidm`: `https://openreview.net/forum?id=XqjuAdSVFq`
    → `https://arxiv.org/abs/2604.25297`
  - `lee2026clear`: already `https://arxiv.org/abs/2604.05821` (matches) — no change.
- **Entry ordering inside `papers.bib`** = the order they should appear within
  each category, mirroring `resume.tex`. Because the page uses
  `--group_by none`, jekyll-scholar preserves file order. Order:
  - Conference: SIGIR2026 → ICLR2026 → LEGALMIDM → CLEAR → ACL-SRW2025 → EMNLP2024
  - Domestic: KURE(HCLT2025) → KoE5(HCLT2024)
  - Preprint: MLAIRE → MIMO → SHIFT → jang2025crosslingual → VAETKI

**`_pages/publications.md`** — replace the single `{% bibliography %}` with
three labeled sections, keeping the existing bib-search include:

```liquid
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

(Exact heading markup — `##` vs `<h2>` — finalized during Docker verification to
match al-folio publications styling. The `--query @*[field=value]*` filter is
confirmed supported by this al-folio version via
`_includes/selected_papers.liquid`.)

**`_config.yml`** — add `category` to `filtered_bibtex_keywords` so it does not
appear in the BibTeX popup. This is the only `_config.yml` change.

### 4.2 Content sync

| File                   | Change                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `_pages/about.md`      | Rework the research paragraph to match resume **Research Summary**: dense/sparse/late-interaction retrieval, multilingual IR, RAG; venues SIGIR/ICLR/ACL/EMNLP; contributions to sentence-transformers & MTEB; "200+ GitHub stars and **1.3M+** cumulative Hugging Face downloads". Keep bio paragraph (NLP&AI Lab, Prof. Heuiseok Lim, Hongik double major) and the open-source list (keep FlagEmbedding & InstructKR). |
| `_pages/opensource.md` | Add to Sentence-Transformers: **EmbedDistillLoss** (`PR #3665`). Add new section **InstructKR (2026)**: led Korean Reranker evaluation & leaderboard project — link `https://github.com/instructkr/reranker-simple-benchmark`. Keep existing FlagEmbedding section.                                                                                                                                                      |
| `_pages/projects.md`   | KURE bullet: `1.1M+` → **`1.3M+`**; align wording to resume (add WBL HF link `https://huggingface.co/NC-AI-consortium-VAETKI/VAETKI` if consistent with existing style).                                                                                                                                                                                                                                                 |
| `_projects/kure.md`    | `1.1M+ cumulative downloads` → **`1.3M+ cumulative downloads`**.                                                                                                                                                                                                                                                                                                                                                         |
| `_data/cv.yml`         | Full rework (see 4.3).                                                                                                                                                                                                                                                                                                                                                                                                   |
| `_pages/cv.md`         | Remove the `cv_pdf:` front-matter line entirely (drops demo PDF button). Replace placeholder `description` with a real one. Set `nav: true` so CV appears in the navbar. Keep `cv_format: rendercv` and `toc.sidebar: left`.                                                                                                                                                                                             |
| `_news/news_*.md`      | Optional, additive: add news items for ICLR 2026 (Cross-Lingual Alignment), ACL 2026 (CLEAR), and HCLT 2025 Best Oral (KURE). Existing `news_1` (SIGIR 2026) and `news_2` (LEGALMIDM) unchanged.                                                                                                                                                                                                                         |

### 4.3 `_data/cv.yml` rework

Keep the existing rendercv schema/shape (proven to render). Changes:

- `label`: keep `NLP Researcher` (or `Retrieval Researcher & Engineer` to match
  resume tone — final wording decided in implementation, low-risk).
- `summary`: replace with the resume **Research Summary** condensed to 1–2
  sentences.
- `social_networks`: keep GitHub; keep LinkedIn (real, harmless); GitHub
  username `yjoonjang`.
- `sections`:
  - **Education**: keep both entries; fix Hongik `end_date` to `2025`
    (resume: Feb. 2025). Korea University M.S., NLP&AI Lab, Prof. Heuiseok Lim.
  - **Publications [Conference]**, **Publications [Domestic Conference]**,
    **Preprint**: three sections mirroring resume, listing title / authors
    (Youngjoon Jang bold per resume) / venue / year, in resume order. Use the
    rendercv entry shape already used for `Awards` (title/authors/date/...) or
    plain bullet highlights — whichever renders cleanly (verified in Docker).
  - **Open Source Contributions**: Sentence-Transformers, MTEB, InstructKR
    (mirror `opensource.md`, including EmbedDistillLoss & InstructKR; keep
    FlagEmbedding).
  - **Projects**: WBL, KURE, Korean ColBERT & Sparse Retrievers, KT–KU Legal
    LLM, PreRanker, URACLE (mirror `resume.tex` Projects, 1.3M+ for KURE).
  - **Technical Skills**: replace the wrong entries
    (Django/FastAPI, Next.js/React, AWS) with resume's:
    - Languages: Python, Bash, SQL
    - Machine Learning: PyTorch, Hugging Face (Transformers,
      Sentence-Transformers, Accelerate), vLLM
    - Infrastructure & Tools: Docker, Linux, Git, Weights & Biases
  - **Awards**: keep (HCLT 2025 Best Oral Presentation — KURE).
  - **Languages**: keep (Korean native, English fluent).

## 5. Data Flow

Static content edits → Jekyll build (Docker) → visual verification at
http://localhost:8080 → `npx prettier . --write` → done. No runtime logic.

## 6. Verification (acceptance criteria)

1. `docker compose up --build` completes with **no Jekyll/scholar build errors**.
2. `/publications/`: exactly three sections in order
   (Conference → Domestic → Preprint); each entry in the correct category and
   in resume order; new MLAIRE/MIMO/SHIFT visible under Preprint; bib search
   still works.
3. `/cv/`: renders without error; shows reworked Skills, the three Publications
   categories, Open Source, Projects; **no PDF button**; appears in navbar.
4. Site-wide grep: **zero** occurrences of `1.1M` or `1.2M` for HF downloads;
   `1.3M+` used consistently.
5. No broken internal links; ICLR/LEGALMIDM links match resume.
6. Dark mode and navbar render correctly on `/`, `/publications/`, `/cv/`,
   `/projects/`, `/opensource/`.
7. `npx prettier . --write` applied; build still green afterward.
8. `resume.tex` remains untracked and unmodified.

## 7. Risks & Mitigations

- **jekyll-scholar query/heading rendering**: `--query @*[category=...]*` is
  confirmed available; exact heading markup tuned during Docker verification.
- **rendercv section shape for Publications**: reuse a known-good entry shape
  (Awards-style); verify in Docker before finalizing.
- **Missing `preview` images for new bib entries**: thumbnails degrade
  gracefully; acceptable. Optionally omit `preview` for the 3 new preprints.
- **resume.tex internal inconsistency (1.3M vs 1.2M)**: resolved by user
  decision → always `1.3M+`.

## 8. Out of Scope / Follow-ups

- Real resume PDF: user may later compile `resume.tex` externally and drop
  `resume.pdf`; re-adding a `cv_pdf` link is a trivial future change.
- Updating `repositories.yml` to real repos (kept as demo per user decision).
