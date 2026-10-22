# Will This Work on My Machine

Honest answer first: any computer made in the last ten years can run *a* local AI model. The variable is not whether it works but how well. This chapter gives you the numbers and a two-minute way to learn what your machine actually has.

## The only three numbers you need

- **RAM** (memory): decides how big a model you can load at all.
- **Free disk space**: models are files, typically 1-5 GB each for modest ones.
- **CPU age**: decides how fast answers appear. A GPU is a bonus, not a requirement.

Everything else — brand, OS, laptop vs desktop, gaming rig vs office machine — is detail.

## Find your RAM in under a minute

Windows: press `Ctrl`+`Shift`+`Esc` to open Task Manager, click the Performance tab, and look at Memory. You will see something like "8.0 GB DDR4".

macOS: click the Apple menu, choose About This Mac, and read the Memory line.

Linux: open a terminal and run:

```bash
free -h
```

The `Mem:` row under `total` is your number.

For disk space, Windows shows it under Settings then Storage, macOS under About This Mac then Storage, and Linux users can run:

```bash
df -h ~
```

## The RAM table, in plain numbers

Model names carry a size hint. The "B" means billion learned parameters — think of it as rough intelligence units. The bigger the B number, the more RAM you need:

| Your RAM | Model class that fits | What it feels like |
| --- | --- | --- |
| 4 GB | 0.5B to 1B | Surprisingly capable, short answers, works slowly |
| 8 GB | 1B to 3B, comfortably | Good chat quality, readable speed |
| 16 GB | 7B to 8B | This is the sweet spot for local AI |
| 32 GB | 13B to 27B | Clearly smarter, still usable speed |
| 64 GB and up | 70B class | Cloud-comparable quality, but slow on old CPUs |

Two footnotes so the table stays honest:

- The numbers assume the standard compressed "Q4" models from chapter 4 — the ones Ollama downloads by default.
- Keep about 2 GB of RAM free for your operating system and browser. An 8 GB machine busy with Chrome plus Slack has less for the model than the sticker suggests.

## Is a GPU needed?

No. Ollama runs fine on CPU alone; it just talks slower per word. A modest 1B-3B model produces readable answers on CPU even on older machines. Dedicated NVIDIA/AMD video cards or Apple Silicon chips *speed things up*, and Ollama uses them automatically when present, but nothing in this book requires buying anything.

Apple Silicon Macs (M1/M2/M3/M4) handle local AI gracefully because the memory chip and the processor live on the same silicon. An M-series chip with 16 GB of unified memory behaves like a 16 GB machine with a built-in accelerator.

## Can a very old laptop do anything useful?

Yes, with expectations set correctly. A 2014-era machine with 8 GB of RAM will happily run a 1B or 3B model. Answers stream in at a calm pace, similar to typing speed of a friend texting you. Great for drafting and questions, not for instant responses.

## The sanity check

Before moving on, write down (or keep in mind) your two numbers:

1. My total RAM is ___ GB.
1. My free disk is at least ___ GB (you will want about 10 GB to be comfortable).

Take those numbers to chapter 3 — [Installing Ollama](03-install-ollama.md) — and to the pre-flight list in the back of the book, the [Hardware Checklist](10-hardware-checklist.md).
