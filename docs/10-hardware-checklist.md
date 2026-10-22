# Hardware Checklist

One page, printable, pre-flight for everything in this book. Tick from top to bottom; stop and fix when a box will not tick.

## Before you install

- [ ] I know my RAM: ___ GB (chapter 2 says how to check in one minute).
- [ ] I know my free disk: at least 10 GB free.
- [ ] I picked my budget model class from the RAM table (1B-3B for 8 GB machines, 7B-8B for 16 GB).
- [ ] I have a working internet connection right now, for the downloads only.

## Install day

- [ ] Ollama installed (`ollama --version` prints a version).
- [ ] First model pulled (`ollama list` shows at least one model and a size).
- [ ] Terminal chat works (`ollama run <model>`, say hello, then `/bye`).
- [ ] I know the exit command (`/bye`) and the stop command (`ollama stop <model>`).

## The daily-use layer

- [ ] Desktop chat app installed and connected (GPT4All, Open WebUI, LM Studio, or Chatbox from chapter 6).
- [ ] App points at Ollama (`http://localhost:11434`) and shows my models.
- [ ] Telemetry setting audited (off, unless I decided otherwise on purpose).
- [ ] Chat history location known (app settings or a cloud-unsynced folder).

## Privacy and trust checks

- [ ] Airplane-mode test done: with the network off, a chat still answers.
- [ ] I decided what never goes into a prompt (my line: no real patient or client records, no passwords, no account numbers).
- [ ] A factual answer was verified once and caught (or trusted after checking) — the habit, not the example, is the point.

## Housekeeping

- [ ] Two favorite models kept, others removed (`ollama rm`) to keep disk friendly.
- [ ] `ollama ps` understood: nothing sits in RAM after my session.
- [ ] Book site built locally with `python3 scripts/pipeline.py` so help is always available offline.

## When you outgrow this starter setup

Signs to recognize, gently:

1. You wait minutes on every 7B answer on an old CPU, and you want 8B speed daily: a used 16 GB RAM machine (or Apple Silicon) is the single best upgrade.
1. Your disk fills with experiments: rotate with `ollama rm`, same as a bookshelf.
1. You start locally hosting for other people: reread chapter 7 about 0.0.0.0 and accounts, then reread it once more.

That completes the book proper. The appendix of commands lives in chapter 5; the why of everything lives in chapter 1; the honest boundary between systems lives in chapter 8.
