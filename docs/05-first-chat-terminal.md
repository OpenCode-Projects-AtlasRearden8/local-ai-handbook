# Your First Chats in the Terminal

The terminal is a plain window where you type commands. Chapter 3 had you open it once; here is the longer version, plus your first real conversations.

## Opening the terminal on your system

- Windows: press `Win`, type `powershell`, press Enter. (Anything labelled Terminal or PowerShell works.)
- macOS: press `Cmd`+`Space`, type `terminal`, press Enter.
- Linux: `Ctrl`+`Alt`+`T` on most desktops.

First command, re-checking that the app is alive:

```bash
ollama --version
```

Two things beginners trip on, both harmless: you do not need to move into any special folder to use `ollama`, and leaving a chat is not the same as closing the window — see `/bye` below.

## Start a conversation

One command does the rest: it finds the model on disk (or downloads it first) and opens a chat:

```bash
ollama run llama3.2
```

First run looks roughly like this:

```text
pulling manifest
pulling 2e5a41... 100%
success
>>> Send a message (/? for help)
```

Type in plain English, press Enter, and the answer streams in word by word. Ask short questions for quick answers; state when you want depth.

Leaving the chat:

```text
/bye
```

Other useful in-chat slash commands:

- `/clear` — empties the conversation memory and starts fresh.
- `/show info` — prints facts about the loaded model.
- `/set system ...` — a standing instruction the model keeps using; quietly powerful (below).
- `/?` — the built-in list of everything else.

## Paragraphs and multi-line input

Enter submits in a terminal, so longer writing needs a different trick. Triple quotes hold a paragraph:

```text
"""This is the text I want checked
for clarity and tone."""
```

## Change the personality (system prompts)

Locally you own the assistant, so give it a standing order. Inside a chat:

```text
/set system You explain things like a patient friend, in short sentences, never using jargon without defining it.
```

Keep the conversation as its own reusable helper:

```text
/save my-friendly-helper
```

Then later, from a fresh terminal:

```bash
ollama run my-friendly-helper
```

That is your first custom model: one command, no coding, and it behaves however you told it to.

## Asking better questions (prompts 101)

Three habits make modest models sound brilliant:

1. Say the role and the ask in one sentence: "Explain RAM to me like I have never opened a computer."
1. Give the shape of the answer: "in five sentences" or "as a short list".
1. Ask one thing per turn. Small models do better stepwise than with ten-part mega-prompts.

If an answer comes back wrong, ask a follow-up ("Check that again and correct anything that is wrong"). A second pass is often cleaner, and it costs nothing because there is no meter running.

## Managing models from outside a chat

All of these run from a fresh terminal prompt, not inside a conversation:

```bash
ollama list
ollama ps
ollama stop llama3.2
ollama rm llama3.2
ollama cp llama3.2 my-new-name
```

What each does:

- `list` — models on disk, with sizes.
- `ps` — what is held in RAM right now.
- `stop` — unloads the model immediately (it also unloads itself after about 5 idle minutes).
- `rm` — deletes the file, freeing disk.
- `cp` — renames your saved experiments.

## How fast, honestly?

Modern-ish hardware streams a 3B model at a readable speed, roughly 10-30 words per second. A 7B-8B model on an older CPU is more like 3-8 words per second: tolerable for drafting, slow for snappy back-and-forth. If speed irritates you, go down one B-size; if quality frustrates you, go up.

Once a conversation feels natural, install the comfortable window: [A Free Chat Window](06-chat-uis.md).
