# Installing Ollama

Ollama is a free, open-source app that runs AI models on your computer. It does three jobs: keeps models organized in one place, gives you a tiny command line (chapter 5), and offers a local API that chat apps connect to (chapter 6). Pick your operating system below.

Before starting, confirm you have about 1 GB free for the app plus room for at least one model (chapter 2's table), and a working internet connection — for downloads only. After installation, everything runs without a network.

## Windows 10 or 11 (64-bit)

The easy path is the official installer:

1. Visit `https://ollama.com/download` and click the Download for Windows button.
1. Run the downloaded setup file like any other installer. It is fast and quiet; the app installs to your normal Programs list and an icon appears near the clock.
1. Open PowerShell. Press `Win`, type `powershell`, and press Enter.
1. Confirm it works:

```powershell
ollama --version
```

If a version like `ollama version is 0.x.x` prints, you are done. If PowerShell says it does not recognize the command, close and reopen PowerShell once — installers sometimes update the search path after the first window opens.

Comfortable with `winget`? One line does the same job:

```powershell
winget install --id Ollama.Ollama -e
```

## macOS

This works the same on Intel and Apple Silicon Macs:

1. Visit `https://ollama.com/download` and click the Download for macOS button. Your Mac downloads a `.dmg` file.
1. Open the `.dmg`, drag the Ollama app into your Applications folder, and launch it.
1. On first launch, macOS may ask permission to run it; click Open.
1. Open Terminal. Press `Cmd`+`Space`, type `terminal`, and press Enter.
1. Confirm it works:

```bash
ollama --version
```

The menu-bar app conveniently runs the background service for you, including after restarts.

If you already use Homebrew, this line is equivalent and quieter:

```bash
brew install ollama
```

## Linux

Ubuntu, Debian, Fedora, and most other distros have a one-line official install script:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

> About that command: it fetches Ollama's official install script over HTTPS and runs it immediately. Piping scripts this way is common, and you can read the script first at that URL if you prefer. It installs a `systemd` service so the background service starts on boot.

When it finishes, confirm:

```bash
ollama --version
```

Manual alternative without the pipe: download the `.tgz` for your architecture from the releases page at `https://github.com/ollama/ollama/releases`, unpack the binary onto your path, and run `ollama serve` (no systemd needed). The script route is simply the least friction.

## Where the app actually lives

Two pieces install, and knowing their names un-mystifies everything later:

- The app you launch by hand from the terminal: `ollama`.
- The quiet background service that loads models into memory on request: `ollama serve`. The Windows and macOS installers manage it for you.

On Windows, the tray icon near the clock is the service. On macOS, the menu-bar icon is the service. On Linux, systemd owns it: `systemctl status ollama` shows whether it is alive.

## If something goes wrong

Common and solvable:

- "command not found" — close the terminal and open a fresh one; the installer updates your PATH.
- Download hangs or stalls — delete the partial file with `ollama rm <model>` and let it pull again.
- The service will not start on Linux — run `ollama serve` directly to see the error text.
- Corporate laptop locked down? Fine to ask IT; this is ordinary open-source software with no telemetry in the app itself.

Installed and verified? Continue to [Choosing Your First Models](04-choosing-models.md) — then meet it in the terminal in [Your First Chats](05-first-chat-terminal.md).
