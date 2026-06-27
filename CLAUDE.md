# Vascular Surgery Exam Prep - Project Guide

## Overview

Quarto Book project — a vascular surgery board exam prep e-book companion to the Audible Bleeding podcast. Outputs HTML (primary) and PDF. Published via Quarto Pub.

Current version: v01.26 (tagged in git). Working toward second edition.

## Build

```bash
quarto render          # Full build (HTML + PDF)
quarto preview         # Local dev server
```

Requires R with the `embedr` package installed (used for podcast audio embeds).

## Project Structure

- `_quarto.yml` — Book configuration, chapter order, bibliography, format settings
- `index.qmd` — Preface (version number lives here)
- `authors.qmd` — Contributors list
- `references.qmd` — Auto-generated bibliography page
- `references.bib` — BibTeX bibliography (~14K lines)
- `images/` — Figures and cover art
- Chapter files are `.qmd` in the repo root, organized by anatomical section in `_quarto.yml`

### Chapters by Section

| Section | Files |
|---------|-------|
| Head and Neck | cerebrovascular.qmd, trauma-cerebrovascular.qmd |
| Upper Extremity | upper-extremity.qmd, tos.qmd, hemodialysis.qmd |
| Thorax | dissection.qmd, taaa.qmd, aortopathies.qmd, trauma-endovascular.qmd |
| Abdomen | abdominal-aneurysms.qmd, mesenteric.qmd, renal.qmd, trauma-arterial.qmd, trauma-venous.qmd |
| Lower Extremity | claudication.qmd, clti.qmd, ali.qmd, venous-disease.qmd, trauma-peripheral.qmd |
| General | vascular-lab.qmd, radiation.qmd, endovascular.qmd, rapid.qmd |

## Content Conventions

### Chapter Header Template

```markdown
# Chapter Title {#sec-chapter-id}

Authors: *First Last and First Last*

Contributors: *First Last*

```{r echo=FALSE}
library(embedr)
embed_audio("https://traffic.libsyn.com/audiblebleeding/episode_url.mp3")
```
```

### Formatting Rules

- **Headings**: Use `#` through `####`. Always add section IDs on level-1 headings: `{#sec-kebab-case-id}`
- **Q&A style**: Bold the question, plain text for the answer:
  ```markdown
  **What is the recommended treatment?**
  Answer text here.
  ```
- **Bold terms**: Use `**term**` for key terms, `***term***` for emphasized definitions
- **Lists**: Standard markdown. Indent sub-items with 4 spaces. Nesting can go deep (up to 9 levels supported in PDF)
- **Figures**: `![](images/filename.png){fig-align="center"}`
- **Tables**: Markdown pipe tables with caption below: `: **Table Title** - description`
- **Citations**: `[@bibtexkey]` or `[@key1; @key2]` for multiple
- **Cross-references**: `@sec-section-id` to link between chapters
- **Callouts**: Use Quarto callout syntax for tips, notes, warnings:
  ```markdown
  ::: callout-tip
  ## Take a Listen
  Content here
  :::
  ```

### Style Guidelines

- Write in clinical, exam-focused tone
- Follow progressive structure: overview, pathophysiology, evaluation, management
- Cite landmark trials by name (e.g., STILE, TOPAS, CREST)
- Keep file names kebab-case
- Add new images to `images/` directory
- Add new bibliography entries to `references.bib` in BibTeX format

## Workflow for Second Edition

- First edition is preserved at git tag `v01.26`
- Create feature branches off `main` per chapter: `update/chapter-name`
- Open PRs back to `main` for review
- Update version in `index.qmd` when releasing
