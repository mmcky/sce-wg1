# SCE WG1 — Language and Formal Semantics

Public coordination space for **Working Group 1 (Language and Formal Semantics)** of the Society for Computational Economics, formed at CEF 2026 in Venice. Sponsored by SCE and partnered with [Econ-ARK](https://econ-ark.org) and [QuantEcon](https://quantecon.org).

**Website:** https://mmcky.github.io/sce-wg1/

**Co-chairs:** Akshay Shanker and Matt McKay

## What the group does

Structural economics has no standard, shareable representation of a dynamic model together with its computational solution. WG1 works toward economic models that machines can read, manipulate, and verify — a formal account of what a model file *means*, stated by the people who build the toolkits.

The group runs two complementary projects:

| Project | Description |
| --- | --- |
| **A — The Semantics of Economic Models** | Each toolkit team states formally what its model files mean, publishing a per-toolkit paper; building toward a journal special issue. [Project page](https://mmcky.github.io/sce-wg1/project-a.html) |
| **B — A Community Library of Baseline Models** | A standardized repository of the community's baseline models in existing notation, with each toolkit's treatment documented side by side. [Project page](https://mmcky.github.io/sce-wg1/project-b.html) |

Project B grew out of a proposal put to the CEF 2026 pre-conference; it is coordinated by Matt McKay, with QuantEcon hosting and publishing the collection.

The Project A special-issue proposal lives in [`project-a/`](project-a/). [`special-issue-proposal.md`](project-a/special-issue-proposal.md) is the **single source** for both the Project A page and the downloadable PDF — edit the markdown, never the generated HTML:

```
cd tools && npm install     # once
npm run build               # regenerates the page and the PDF
```

This writes `docs/project-a.html` (the page, in the shared site chrome) and `docs/special-issue-proposal.pdf` (typeset via the LaTeX template in [`templates/`](templates/)). Use `npm run build:no-pdf` if you don't have a LaTeX distribution installed; the previously built PDF is then reused.

You don't have to run any of this to change the proposal. Both outputs are generated in CI by [`.github/workflows/publish.yml`](.github/workflows/publish.yml) on every deploy, so they are **not committed** — edit the markdown and open a pull request, and the workflow attaches the rendered page and PDF to the run for review. Building locally is only for a faster preview.

Drafts for the Project B specification process live in [`project-b/`](project-b/):

| File | Purpose |
| --- | --- |
| [`capability-survey.md`](project-b/capability-survey.md) | Proposed survey content, written for co-chair review and then transcription into a form. Completed once by each project; the responses compose the capability matrix that determines which baselines a group can adopt. |
| [`model-spec-template.md`](project-b/model-spec-template.md) | Skeleton for a baseline specification, authored per group by a model specification architect. Implementations and tutorials are submitted against a frozen version. |

## This repository

- Hosts the working group website (served from [`docs/`](docs/) via GitHub Pages).
- Acts as the group's public coordination space — use the issue tracker for questions, suggestions, and discussion.

## Joining

The group works in the open, but membership is by invitation from the co-chairs — this keeps the author set coherent across Project A. If you work on the language and semantics of economic models, register your interest via the issue tracker or email the co-chairs.

You do not need to be a member to follow along: this repository and its issue tracker are open to everyone.

<!--
TODO before announcing the site:
- Replace the placeholder address (wg1@example.org) in docs/index.html and docs/project-b.html
  with both co-chairs' contact addresses. Correspondence is sent personally by the co-chairs;
  no shared wg1@ address and no mailing list are being created, so the footer "Mailing list"
  entry stays tbd. (The Project B CTA may want the coordinator's address alone rather than both.)
- Add the Project B collection repository link once it exists — docs/project-b.html marks it
  ⟨link to follow⟩ in the Contributing section.
- Add the sign-up form link when it exists, and the when2meet availability grid.
- Finalise the Project A description (AAS).
- Add a CODE_OF_CONDUCT.md and link it from the site footer.
-->
