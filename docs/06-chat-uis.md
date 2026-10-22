# A Free Chat Window You Can Double-Click

Typing commands is a skill, but most people switch to a chat window after a week and never go back. This chapter installs a free desktop app and connects it to Ollama, the way a music player connects to your music folder.

## The short version

A local chat app is a face for the same engine. The model still runs on your machine through Ollama; the window is just a nicer place to type. That also means the app can be uninstalled or replaced without losing anything — your models live in Ollama, not in the window.

## Option A: GPT4All, designed for ordinary laptops

GPT4All is a free, open-source desktop app for Windows, macOS, and Linux, built around modest hardware. Its extra superpower, LocalDocs, lets you ask questions about a folder of your own files — with the search done locally.

1. Download the installer from `https://gpt4all.io` and run it like any desktop program.
1. On first run, the app offers a model catalog. Pick a small one (look for a Llama 3.2 1B or 3B GGUF entry, or a 1B-3B size pattern from chapter 4) and download it.
1. Chat. That is genuinely the whole procedure.

Useful first settings (gear icon):

- Turn off any "anonymous analytics" or "telemetry" toggle if one is enabled by default.
- Try LocalDocs: point it at a folder, wait for the local index to build, then ask "summarize the main points of these documents".

Honest note: GPT4All downloads models in its own format, separate from Ollama's. Two catalogs, two disk shelves. Keeping one favorite model in each avoids clutter.

## Option B: Open WebUI, the power option in a browser tab

Open WebUI is a free, self-hosted web page that runs on your own machine and talks to Ollama automatically. It gives you chat history, folders, model switching, and a modern look. It needs a bit more setup, hence "power option".

If you have Docker installed:

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

Then open `http://localhost:3000` in a browser, create a local account (stored on your machine; it is for this page only, not a cloud account), and start chatting. It finds Ollama at `http://localhost:11434` on its own.

No Docker? A Python route works too:

```bash
pip install open-webui
open-webui serve
```

Then the same address: `http://localhost:8080`.

> Keep this for yourself. Open WebUI is a multi-user chat server: on a home network anyone who can reach your IP and port could use it. Keep it on localhost, do not port-forward it to the internet, and always have a password set if other people share your network. The privacy chapter revisits this at [The Privacy Trade-Offs](07-privacy-tradeoffs.md).

## Option C: one-window alternatives

Two more free desktop apps work nicely and connect to Ollama directly, with no server setup:

- LM Studio (`https://lmstudio.ai`): polished catalog and its own model engine; free but not open-source, and it prefers its own downloaded models rather than Ollama's.
- Chatbox (`https://chatboxai.app`): clean desktop client that plugs into a local Ollama server: install, pick a model from its dropdown, chat.

All three are honest free options. Pick by feel — the model does the thinking either way.

## Comparison at a glance

| App | Install effort | Runs models | Owns a special feature |
| --- | --- | --- | --- |
| GPT4All | Double-click installer | Downloads its own | LocalDocs over your folders |
| Open WebUI | Docker or pip command | Uses Ollama's | Browser multi-chat workspace |
| LM Studio | Double-click installer | Its own engine | Polished catalog, tuning sliders |
| Chatbox | Double-click installer | Uses Ollama's | Simplest connect-to-Ollama flow |

## Connecting any client to Ollama 1-2-3

Whatever window you like, the handshake is the same idea:

1. Start Ollama (the background service installs run automatically on startup).
2. In the app's settings, point it at `http://localhost:11434` (Open WebUI and Chatbox find it alone).
3. Choose a model you have already pulled with `ollama pull` from chapter 4.

## When to just stay in the terminal

Fair question, since the terminal chapter just before this works fine. Keep the terminal for: quick scripts and one-shot questions, running with computer maximized and screen tiny, and `/save`-ing custom personalities fast. Keep a window for: long conversations, pasting big text, and daily drafting.

With a window running, the last two chapters matter most, so read [The Privacy Trade-Offs](07-privacy-tradeoffs.md) with your new app open and the settings in front of you.
