# Glossary

Plain-English definitions, alphabetized, one paragraph each. If a term in another chapter confused you, it is probably here.

## A

**Assistant** — what you get when a model is wrapped with instructions ("be helpful, be brief") and a chat window. The model is the brain; the assistant is the personality and manners.

**Anchor (URL anchor)** — the `#token` part of a web page address that jumps to a specific heading. Used throughout this site's chapters for deep links.

## B

**B number** — the size shorthand on models (1B, 3B, 8B, 70B). Roughly, a count of the model's learned parameters, which tracks with how smart it is and how much RAM it wants.

## C

**CPU** — the computer's main processor. Every machine has one; every model can run on it, just slower than on a GPU.

**Context window** — a model's working memory for one conversation: everything it "sees" at once, measured in tokens. Small models have small windows; long chats overflow and older lines get forgotten.

## D

**Disk (storage)** — permanent space, like a bookshelf. Model files live here. Fill it and you can `ollama rm` models you are not using, from chapter 4.

## G

**GGUF** — the file format modern small models ship in on your disk. You will see the word in model catalogs; treat it as "the AI file type".

**GPU** — the graphics chip. Game cards and Apple Silicon make local AI noticeably faster, but are optional for everything in this book.

**GUI** — graphical user interface: any app with windows and buttons, as opposed to the terminal's typed commands. Chapter 6 installs several.

## H

**Hallucination** — a confident wrong answer. Models, big and small, sometimes invent facts smoothly. There is no switch that turns it off; asking for sources and checking claims is the practical defense.

## I

**Inference** — actually running the model: prompt in, prediction out. When Ollama is "thinking", it is doing inference.

## K

**Keep-alive** — how long a loaded model waits in RAM before Ollama unloads it automatically (about 5 idle minutes). You can see what is loaded with `ollama ps`.

## L

**Local vs autoload** — nothing formal; a friendly reminder that "local" describes the software running on *your* machine. Chapters 1 and 8 make the trade-off case.

**Localhost** — the address your machine uses for itself, like `http://localhost:11434`. A UI on localhost is visible only to you, not the network or internet.

**LLM** — large language model, the text-in-text-out AI behind chat assistants. All models named in this book are small LLMs.

## M

**Modest model** — this book's working term for models sized for ordinary computers (about 1B-8B), as opposed to data-center class models. Suggested picks live in chapter 4.

## O

**Ollama** — the free app this book standardizes on. Manages model files, exposes a terminal command, and provides the local API that chat windows connect to at `http://localhost:11434`.

**Open source** — software whose code anyone may read, modify, and share under a license. Ollama and GPT4All are open source; some AI *models* describe themselves as "open weights" while keeping training details closed — both kinds run fine locally.

## P

**Parameter** — one adjustable knob inside a model: a learned number. Billions of parameters is what the B suffix counts. Also the word for settings like `temperature` when you set them on a model — different sense, same name, confusing, sorry.

**Prompt** — whatever you type to the model. **System prompt** is the standing instruction that shapes all replies in a session (chapter 5 shows `/set system`).

## Q

**Quantization (Q4, Q8)** — compressing a model's internal numbers so the file and RAM use shrink (Q4 = 4 bits per weight). You download Q4 by default; the quality cost is small for everyday use.

## R

**RAM** — working memory; a model must be fully loaded into RAM to run, which is why chapter 2's table maps RAM size to model B-size.

**RAG (retrieval-augmented generation)** — "search your own files first, let the model answer from what was found." GPT4All's LocalDocs is the friendly example in chapter 6.

## T

**Telemetry** — optional usage reports sent by an app to its maker. Check settings; local-first apps tend to default it off.

**Terminal** — the window where typed commands go. Chapter 5 is your full tour; you only ever need a small handful of commands.

**Token** — the word-fragment units models read and write. For plain English, one token is roughly three-quarters of a word: useful for understanding context-window numbers and why long chats raise RAM use.

## U

**Unload** — remove a model from RAM (not from disk). Happens automatically after idle time; `ollama stop` does it immediately when you want the memory back.
