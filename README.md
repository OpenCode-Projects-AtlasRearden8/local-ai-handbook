# The Local AI Handbook

A plain-English, step-by-step manual for running AI on your own computer — written the way a friend would explain it: no condescension, honest trade-offs, tested commands.

Published as a free resource by [Asdale Dynamics, LLC](https://dylanasdale.github.io), the beginner-friendly AI education project of author Dylan Asdale.

## What is inside

- **docs/** — the handbook itself, one Markdown file per chapter:
  - Why run AI locally (privacy, offline use, no subscription)
  - Hardware and RAM guidance, with a RAM-to-model-size table
  - Installing **Ollama** on Windows, macOS, and Linux
  - Choosing modest models for old hardware
  - First chats in the terminal, slash commands, and system prompts
  - Free desktop chat UIs (GPT4All, Open WebUI, LM Studio, Chatbox)
  - The privacy trade-offs, stated plainly in both directions
  - When local beats the cloud (and when it really does not)
  - A **glossary** in plain English
  - A printable **hardware checklist**
- **scripts/pipeline.py** — a standard-library-only static site builder. It converts the chapters into a polished, offline-friendly HTML site: chapter pages, a landing page, and a single "whole book" page ready to print or Ctrl+F.
- **tests/** — unit and integration tests for the converter, builder, CLI, docs lint, and repo hygiene.
- **site/** — the generated site (built locally; not committed).

## Quick start

View the book as plain text:

```bash
# any Markdown viewer
less docs/00-introduction.md
```

Build the static site (requires Python 3.9+, nothing else):

```bash
python3 scripts/pipeline.py
```

Then open `site/index.html` in any browser. Works with no web server and no network: the site makes zero external requests.

Check the whole book in one page:

```bash
open site/book.html
```

Lint the documentation (internal links, anchors, structure):

```bash
python3 scripts/pipeline.py --check
```

Convert one chapter to HTML on stdout:

```bash
python3 scripts/pipeline.py --from-md docs/09-glossary.md
```

## Run the tests

```bash
python3 -m unittest discover -s tests -v
```

All tests pass on Python 3.13; the code avoids anything newer than Python 3.9 syntax.

## Authoring notes

Chapters follow a small set of conventions enforced by `pipeline.py --check`:

- Each chapter starts with a `# Title`.
- Internal links point at `.md` files, optionally with `#anchor`; they are rewritten to the built HTML automatically and validated.
- Tables use standard GitHub-style Markdown with divider rows.
- No tabs, no nested-nesting beyond two levels, no blank lines inside lists.

Nothing here tracks you, phone home, or requires an account. The book is designed to be readable from a USB stick.

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 Asdale Dynamics, LLC. You may copy, adapt, and share this material freely, including commercially, with attribution.
