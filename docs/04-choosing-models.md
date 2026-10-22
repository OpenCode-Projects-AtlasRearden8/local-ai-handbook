# Choosing Your First Models

A "model" is the AI brain — a single file, roughly 1-30 GB, holding everything the assistant knows. This chapter teaches you to read the model menu without juggling jargon, using three letters that carry all the meaning: B, Q4, and tokens.

## Reading a model size: the B number

Names like `llama3.2:3b` end with a size like 1b, 3b, 8b, 70b. The B means "billion learned knobs". More knobs means more knowledge and better writing — but also more RAM and slower answers:

- 0.5B-1B: quick, tiny, a bit dim. Great first try on old machines.
- 3B: the everyday workhorse for humble laptops.
- 7B-8B: the classic hobbyist size; noticeably smarter, needs 16 GB.
- 13B-27B: big machines.
- 70B: cloud-adjacent quality; not for old hardware.

Start small. You can always move up; downloading a model sized for someone else's computer is a common beginner mistake.

## The Q4 mystery, kept simple

Inside a model are millions of weights — precision numbers. Files come in "quants" that shrink those numbers: "Q4" stores each with 4 bits. Q4 files are about a third the size of the uncompressed ones and work nearly as well for everyday chat. This default choice is what makes the RAM table in chapter 2 friendly.

You mostly never choose quants; Ollama's default download is Q4 unless you ask otherwise. If you see `Q4_K_M` in a file name, that is a specific (good) 4-bit recipe.

## Tokens: how answers are counted

Models read and write in tokens — word fragments. Free output happens token by token, like a typewriter. RAM also grows with how many tokens you allow a conversation to hold at once; a 3B model holding 4-8 thousand tokens is cheap, 32 thousand gets heavy. Keep chats reasonably short and models small, and RAM stays calm.

## The pick lists

The models listed here are small, free, and proven, drawn from Ollama's library at `https://ollama.com/library`. Download sizes are close: the file you pull is roughly the RAM needed to run it.

| Your RAM | All-round chat | Sharpest multi-step | Strong writing |
| --- | --- | --- | --- |
| 8 GB (or less) | `llama3.2:3b` (2 GB) | `deepseek-r1:1.5b` | `gemma3:4b` (3 GB) |
| 16 GB | `llama3.1:8b` (5 GB) | `deepseek-r1:7b` (5 GB) | `qwen2.5:7b` (4 GB) |
| 32 GB | `gemma3:12b` (8 GB) | `qwen3:14b` | `mistral:7b` (4 GB) |

Notes that prevent confusion:

- Names beginning `llama`, `gemma`, `qwen`, `deepseek`, `mistral`, `phi` are model families: different recipes by different teams, with different personalities.
- `:3b`, `:8b` digits after the colon are size tags inside one family.
- A "thinking" model (`deepseek-r1`) explains its reasoning step by step before answering: nice for math-y questions, chattier for quick asks.

Two honorable mentions if you want a widened horizon: `moondream` (tiny image describer, 1.7 GB) and `smollm2:1.7b` (small but surprisingly articulate). One more honest flag: `tinyllama` is tiny, older, and mostly a curiosity now; prefer the 1B+ models.

## Four commands instead of a college course

Pull a model (download only):

```bash
ollama pull llama3.2:3b
```

Run and chat:

```bash
ollama run llama3.2:3b
```

List what is on disk:

```bash
ollama list
```

Remove something too heavy:

```bash
ollama rm tinyllama
```

## The judgment call, made easy

Pick by purpose, not by fashion:

1. Old machine, first time: `llama3.2:1b` or `llama3.2:3b`.
1. Comfortable 16 GB machine: `llama3.1:8b` is a long-life choice.
1. Writing and drafting help: an 8B or a strong 7B-class model.
1. Explaining and tutoring a beginner: a 3B-4B model is more patient-fitting on hardware.

Try two or three, keep two. Disk space and RAM unload quickly with `ollama rm`, and chapter 5 shows exactly how to swap without headaches.
