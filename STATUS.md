# STATUS

Project: The Local AI Handbook
Owner: Asdale Dynamics, LLC
State: complete and verified (October 2026)

## What was built

A beginner-facing, step-by-step manual for running AI entirely on your own computer, plus the tooling to turn it into a static website.

- **docs/** (11 Markdown files: front matter + 10 numbered chapters):
  - `00-introduction.md` — front matter: audience, conventions, 5-minute quick start.
  1. Why Run AI on Your Own Computer (privacy, offline, no subscription)
  2. Will This Work on My Machine (hardware + RAM table, model-size mapping)
  3. Installing Ollama (Windows, macOS, Linux; verification steps; troubleshooting)
  4. Choosing Your First Models (B sizes, Q4 quantization in plain English, pick lists by RAM)
  5. Your First Chats in the Terminal (slash commands, system prompts, model management)
  6. A Free Chat Window You Can Double-Click (GPT4All, Open WebUI, LM Studio, Chatbox)
  7. The Privacy Trade-Offs (what is and is not protected; health-care education boundary)
  8. When Local Beats the Cloud (task table, money math, speed table)
  9. Glossary (plain-English definitions)
  10. Hardware Checklist (printable pre-flight list with checkboxes)

  All in-text "Chapter N" references follow exactly this numbering, and every cross-reference was checked against the target chapter.
- **scripts/pipeline.py**: standard-library-only static site builder. Zero dependencies, zero network. Produces a landing page, one polished chapter page per chapter with sidebar navigation and prev/next pagers, a single-page "whole book" for printing/Ctrl+F, and a stylesheet (light/dark aware, print styles). `00-` stems are treated as front matter ("Front matter — read this first"), so the on-page "Chapter N of 10" labels match the book's internal numbering.
- **CLI flags**: `--docs/--out` for custom paths, `--from-md FILE` to convert one chapter, `--check` to lint the docs.
- **tests/test_pipeline.py**: 38 tests covering the Markdown converter (headings, inline, links, lists, tasks, tables, fences, escaping), the site builder, the CLI, docs lint, reproducible builds, and repo hygiene (secret-pattern scan, exact MIT LICENSE line, README credit, allowed top-level files).
- **README.md, LICENSE** (MIT, "Copyright (c) 2026 Asdale Dynamics, LLC"), **.gitignore**.

## How to run it

```bash
python3 scripts/pipeline.py            # build site/ from docs/
python3 scripts/pipeline.py --check    # lint docs (links, anchors, structure)
python3 -m unittest discover -s tests  # run the test suite
```

Then open `site/index.html` in a browser — no server needed; the site makes no external requests, so it works offline and from file://.

## Verification results (run in this folder)

- `python3 --version` → Python 3.13.5
- `python3 scripts/pipeline.py --check` → "Checked 11 markdown files: clean"
- `python3 scripts/pipeline.py` → "Built 14 files into .../site" (13 HTML pages + style.css)
- HTML structural check (html.parser tag balance over all 13 generated pages) → 0 problems
- `python3 -m unittest discover -s tests` → 38 tests, OK (0 failures, 0 errors)
- Cross-reference audit: every "Chapter N" mention in docs maps to the correct target chapter
- Secret-pattern scan (API keys, tokens, private-key blocks) across docs/scripts/tests/README/LICENSE → 0 matches
- Reproducible-build test: two consecutive builds produce identical output manifests
- Git initialized with the existing configured identity (Dylan Asdale); repo committed, nothing pushed, no remote

## Fix-ups applied in this pass

- Repo-hygiene test did not allow the `.git` directory (git was initialized after the tests were written); the allowed set now includes it.
- Site builder labeled the front-matter intro "Chapter 1 of 11", which contradicted every in-text chapter reference ("chapter 2's table" = hardware, "Chapter 7" = privacy, and so on). The builder now treats `00-` stems as front matter and numbers the real chapters 1–10, matching the book's own references. Verified on the built pages: intro shows "Front matter — read this first", why-local shows "Chapter 1 of 10", hardware-checklist shows "Chapter 10 of 10".
- Tidied the trip map in `00-introduction.md` (it mixed a restarting numbered list with bullets) and pointed each trip item at its chapter number.
- README: clarified the front-matter/numbered-chapter split and made the "open the whole book" command work on Linux (`xdg-open`) as well as macOS.

## Known gaps

- `site/` is a generated artifact and is gitignored; run `python3 scripts/pipeline.py` after any docs change.
- No full-text search page; use `site/book.html` with browser Ctrl+F (deliberate: no JavaScript, no tracking).
- The Markdown converter is a purposeful subset (no images, footnotes, or definition lists; lists are single-line with one nesting level). Convention violations are caught by `--check` and the tests rather than silently rendered.
- Model names, versions, and download sizes in the chapters are accurate as of October 2026 and clearly labelled as approximate; Ollama's library evolves, so chapter 4 teaches size-reading rather than fixed favorites alone.
- Direct downloads of Ollama/GPT4All/Open WebUI installers were not executed in this environment (none are needed to build or test the repo); installer steps in chapters 3 and 6 follow the vendors' documented flows.
