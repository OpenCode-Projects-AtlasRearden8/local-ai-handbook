# The Privacy Trade-Offs

Local AI is the private option, and this chapter keeps its promises honest, because "private" has edges, and knowing them keeps you safer than a slogan.

## What is genuinely private

When a conversation runs through a local model:

- Your prompts and the model's replies never leave the machine.
- Nothing is uploaded for "training" or "improvement" — no company is on the line because no company receives it.
- Deleting is real. Delete the model and the chat history, and the data is gone rather than "scheduled for removal".

## What still touches the outside world

A local setup is not an airplane in a hangar. Expect these, and judge them like an adult:

- **The model download itself** comes from the internet, so the vendor's server sees that your IP fetched a model once. Your chats are not attached to that event.
- **App settings may include telemetry.** Some desktop apps send optional anonymous usage reports. It is in the settings, plainly labelled; turn it off if it bothers you. Ollama's own app has no such thing by default.
- **Your operating system's normal behavior** continues (crash reports, cloud sync, search indexing). Local AI neither knows nor controls that layer.
- **A browser UI is a web page.** Anything served at `localhost` stays home — unless you deliberately expose it (next section).

## One real way people leak local setups

The name to remember is 0.0.0.0: the "listen on every network interface" setting. Server-style UIs (Open WebUI, a raw `ollama` API on a shared network) become reachable to other machines if you bind them broadly or forward ports. Defaults in this book keep everything on `localhost`. So the safety habits are very short:

1. Do not port-forward your chat UI to the internet.
1. If you do not need the Open WebUI account system, keep it for yourself only.
1. Doubt the setup? Put your machine in airplane mode and re-test.

## Health-care and personal-data boundary

This book's author spent years in nursing, so here is the line stated plainly, and it applies to all AI, local or cloud, in education settings:

- Never enter real patient or client details into any AI system. Local or not, producing a note from real protected data is out of scope for a learning tool.
- Use local AI for *learning*: drafting a study note about diabetic foot care, practicing patient-education language, summarizing a textbook chapter you can already legally see.
- For real patient-adjacent writing, use your organization's own approved tools and policies, which exist already and are the right place.

The same shape of rule applies to business: local protects your drafts; it does not turn a document you had no right to paste anywhere into something safe to paste here.

## The limits of local: what privacy does not buy you

Three things people hope local AI solves, that it does not:

1. **Anonymity.** Your chats stay home, but your ordinary internet traffic follows you as it always has.
1. **Accuracy.** A private wrong answer is still wrong; small models are often confidently wrong. Chapter 5's follow-up habit ("check that again") is the remedy when it matters.
1. **Infection immunity.** Do not paste accounts, passwords, or live credentials into any chat, even local ones. Keep secrets in a password manager, not a prompt.

## A two-minute audit with your own setup

Do it once, tonight:

- [ ] Find the analytics or telemetry toggle in your chat app and note its state.
- [ ] Send a chat with the network off (airplane mode) and see it still works.
- [ ] Search the app's settings for where history is stored, and note the folder.
- [ ] Decide a personal rule for what never goes into prompts (mine: no real names tied to real records, no financial account numbers, no passwords).

Knowing your own rules is worth more than any single app toggle. When you next debate cloud vs local for a job, read [When Local Beats the Cloud](08-local-vs-cloud.md) and let the table decide, not the fear.
