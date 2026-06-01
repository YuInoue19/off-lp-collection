# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A collection of **standalone B2B marketing landing pages (LPs)** in Japanese for a
wholesale / OEM CBD product business. Each page targets a different sales channel and
is built for lead generation (資料請求 / sample request / 導入相談).

| File | Audience | Product focus |
|------|----------|---------------|
| `clinic_index.html` | 医療機関・薬局 (clinics & pharmacies) | CBD capsules / oil for in-clinic sale |
| `fitness_index.html` | フィットネス施設 (fitness facilities) | Premium CBD wellness line + OEM |
| `salon_index.html` | エステ・整体・リラク サロン | Massage oil for treatment + retail |

## Architecture & conventions

- **Each `*.html` is fully self-contained.** All CSS lives in a single `<style>` block
  in `<head>`, and all JS is inline (either a `<script>` block or `onclick` attributes).
  There is **no build step, no bundler, no package manager, and no shared CSS/JS files** —
  edits to one page never affect another. There is intentionally no `index.html` at the root.
- **No external dependencies**, with one exception: `fitness_index.html` loads Google Fonts
  (Noto Sans/Serif JP). `clinic_index.html` and `salon_index.html` use system font stacks only.
- **Language is Japanese** (`<html lang="ja">`), and copy is B2B/wholesale in tone.

### Per-page styling patterns (they differ — match the file you are editing)

- `clinic_index.html` — CSS custom properties named `--primary`, `--accent`, etc.;
  FAQ accordion via inline `onclick="this.parentElement.classList.toggle('open')"`.
- `fitness_index.html` — CSS custom properties prefixed `--color-*` plus `--font-*`;
  FAQ accordion and scroll fade-in (`IntersectionObserver` on `.fade-in`) wired up in a
  `<script>` block at the end of `<body>` via `addEventListener`.
- `salon_index.html` — **no CSS variables** (hard-coded hex values); FAQ via inline
  `onclick`; includes a demo contact `<form>` whose `onsubmit` is `preventDefault()` + `alert()`.

### Placeholders are intentional

Pages ship with fill-in-later placeholders that must be preserved unless explicitly asked to
populate them, e.g. `※ 詳細は資料請求後にご案内いたします`, `[会社名を入力]`, lineup spec
text, and CTA links pointing to `href="#"`. Do not invent real company details, COA data,
prices, or contact endpoints.

### Typical section flow

Pages share a similar narrative (header → hero/first-view → problems → value/solution →
quality assurance → flow → use cases/products → FAQ → final CTA → footer), but section order,
class names, and markup are **not standardized across files**. Read the target file before
editing; do not assume class names from one page exist in another.

## Development

There is no build/lint/test tooling. To preview, open the file directly in a browser, or:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000/clinic_index.html
```

## Deployment

`.github/workflows/pages.yml` deploys to **GitHub Pages on every push to `main`**. It uploads
the entire repository root as the Pages artifact, so each LP is served at its own path
(e.g. `/clinic_index.html`). Adding a new page means adding a new top-level `*.html` file — it
is published automatically on the next push to `main`.
