# When Local Beats the Cloud

Neither choice is a religion. This chapter is a cheat sheet for the actual question: for this task, today, which setup should I open? Sometimes the answer surprises people who have picked one camp.

## The task table

| Task | Best pick | Why, in one sentence |
| --- | --- | --- |
| Private drafts: journals, business plans, personal notes | Local | Nothing is worth exporting to a vendor when the file concerns your own life. |
| Long writing help on modest hardware | Local (3B-8B) | Streaming is slow but steady, and the meter never runs. |
| Summarizing a document you have on disk | Local, or cloud if the doc is huge | A 20-page PDF fits a 3B model fine; a 300-page one does not. |
| Quick explanations and tutoring | Either | Local answers are private and free; cloud is sharper on detail. |
| Fast multi-step reasoning, big math, code debugging | Cloud Today | Top cloud models are clearly stronger at long chains of steps. |
| Fresh web research, current events | Cloud | Local models have a fixed knowledge date. |
| Working on a plane, train, or rural internet | Local | There is literally no alternative offline. |
| Image generation or picture inputs | Cloud mostly | Small machines handle a few image tasks, not pipelines (chapter 4's `moondream` aside). |
| One evening of heavy experimenting with weird prompts | Local | Zero cost per question changes how freely you explore. |
| Anything under a deadline for other people | Cloud Today | Uptime and speed matter more than privacy for shared work. |

The pattern: local wins when privacy, offline use, or flat cost is the deciding factor; the cloud wins when sheer quality, speed, or freshness decides.

## The money math, briefly

A decent cloud assistant is roughly $20 a month, which is $240 a year, forever. A local setup costs the electricity to run your machine (a modest laptop runs a 3B model for pennies of power per evening) plus hardware you already own. The subscription never ends; the model file bought once simply stays.

The honest caveat: you will probably keep a cloud subscription *too*, for the jobs the table keeps handing the cloud. Local does not have to replace cloud to be worth having. Most hobbyists settle on both: one subscription and one on-disk helper.

## The speed equation on old hardware

CPU-only speed on modest machines, in tokens per second and honest feel:

| Model size on a CPU | Rough speed | Feels like |
| --- | --- | --- |
| 1B | 15-50 tokens/s | Snappy chat, no waiting |
| 3B | 8-25 tokens/s | Comfortable reading pace |
| 7-8B | 3-10 tokens/s | Drafting pace, like watching someone type |
| 13B+ | 1-5 tokens/s | Sip-coffee-while-it-writes |

(Apple Silicon and GPUs shift every row up comfortably. Chapter 2 notes which machines have which horsepower.)

The practical translation: prefer local for tasks where you read the output slowly anyway — drafting, summarizing, explaining. Prefer cloud for tasks where many fast round-trips are the point.

## The realism about quality

Set expectations with one example: a 3B local model can explain compound interest clearly but is noticeably weaker at, say, planning a five-city trip with transfers and budget constraints in a single pass. Give it steps instead:

1. Ask for a list of factors to consider.
1. Then ask about one factor at a time.
1. Ask it to recap the combined answer at the end.

Stepwise prompting of a modest model lands closer to a big model's output than most people expect, and chapter 5 covers the habits in detail.

## How knowledge dates work

Cloud models get refreshed; local files are frozen at their creation date. Ask a local model about "the news this week" and it will confidently produce stale plausible text — this is the honest gap for local AI on anything time-sensitive.

One more phrase from the glossary that deserves attention here: hallucination, meaning a confident made-up answer. It happens on cloud *and* local. The check habit — "verify anything factual before you repeat it" — matters everywhere.

## A short rule of thumb

Say it out loud once and you will remember it: if the task involves sensitive text, no internet, or endless experimentation, go local. If it involves fresh facts, tight deadlines, or very long chains of reasoning, go cloud. And when the answer is "I am not sure", try local first: it costs more patience than money.

That closes the judgment chapters. Keep the [Glossary](09-glossary.md) in another tab as vocabulary drifts in, and finish your setup with the [Hardware Checklist](10-hardware-checklist.md).
