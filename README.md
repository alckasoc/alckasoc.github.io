# alckasoc.github.io

Personal site + daily automated reviews of papers from frontier AI labs. Reviews are written as static HTML pages and served via GitHub Pages at the user-site URL.

**Live site:** https://alckasoc.github.io/

## Repo layout

```
alckasoc.github.io/
├── index.html              # Landing page — chronological list of reviews
├── styles/
│   └── main.css            # Shared stylesheet for all pages
├── reviews/
│   ├── _template.html      # Template to copy when authoring a new review
│   ├── assets/             # Per-paper image folders: assets/<paper-slug>/
│   └── <focus>-review-<YYYY-MM-DD>.html
└── .github/workflows/      # (optional) GitHub Actions if running there
```

## How a review is structured

Each review covers papers released in the last ~24h from a fixed list of frontier labs. Pages contain:

1. **TL;DR** — focus of the day's papers, competitiveness vs SOTA, new frontier model releases.
2. **Body** — one `<h1>` per company, one `<h2>` (linked to the paper) per paper, with `<h3>` subsections for Methodology, Evaluation, Ablations, etc.
3. **Embedded figures** — main figures/tables saved to `reviews/assets/<paper-slug>/` and referenced with relative paths.

The depth focuses on methodology, evaluation, ablations, and results. Other sections (intro, related work, conclusion) get briefer bullets.

## Setup

### One-time

Because the repo is named `<username>.github.io`, GitHub Pages is **enabled automatically** on the `main` branch — no Settings → Pages step needed. The site is live at `https://alckasoc.github.io/` as soon as you push.

Confirm the URL works after the first push.

### For the scheduled agent

The agent (running daily in Cowork, Claude Code Routines, or wherever) needs:

- Git credentials with push access to this repo (PAT or SSH key).
- Web search and web fetch capabilities.
- An image-download capability (curl/wget or equivalent).

The full prompt the agent runs is documented in [`PROMPT.md`](PROMPT.md).

## Manual run

To author a review by hand, copy `reviews/_template.html` to `reviews/<focus>-review-<date>.html`, fill in the placeholders, drop images into `reviews/assets/<paper-slug>/`, and update `index.html`'s review list.

## Frontier labs covered

See [`PROMPT.md`](PROMPT.md) for the full list.
