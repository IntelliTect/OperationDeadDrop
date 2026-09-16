# Operation DEADDROP — Stage 1 · Discovery

You are the incident response team at **Nimbus AI**, which runs **DataForge** — a public platform
for hosting and processing machine-learning datasets. At **03:14 UTC** an automated alert fired: a
production data-processing worker made an outbound connection to an unfamiliar domain. It wasn't a
false positive. **Stage 1 is where you find out what happened** — reconstruct the breach from the
logs.

## Your mission
Answer four questions:

1. **How did the attacker get in?**
2. **How did they escalate and move** through the system?
3. **What was taken, and how did it leave?**
4. **How was it nearly missed?**

## Choose your level
Pick **one** based on your comfort with log investigations. Each folder is self-contained — a set
of **logs**, an **architecture diagram**, and a **`BRIEFING.md`**.

| Level | What's different | Time |
|---|---|---|
| [`beginner/`](beginner/) | Two core questions, a starting nudge in the briefing, a scaffolded diagram; some background noise pre-triaged out | 30–35 min |
| [`intermediate/`](intermediate/) | All four questions; some background noise pre-triaged out; neutral diagram | 25–30 min |
| [`advanced/`](advanced/) | The complete dataset — nothing pre-cleared, plus the wider observability feed; all four questions **plus** clear the decoys and scope the incident | 25 min + stretch |

Open your level's **`BRIEFING.md`** to start.

## How to work
- The logs are **noisy on purpose** — most lines are normal activity; a handful tell the story.
- Three files (`cloud-audit.log`, `k8s-audit.log`, `agent-toolcalls.log`) are **JSON, one record
  per line** — grep them, or paste them into your AI assistant to filter and summarise.
- Use the **architecture diagram** to see which component writes which log.
- The `03:14` alert is where the story *ends*, not begins — work backwards from it.
- If your AI assistant refuses to analyse something because it looks malicious, that's a real
  problem defenders face — note it and route around it.

## What you'll produce
A reconstruction of the breach answering the four questions above — the input to Stage 2.

## A note on the data
Every name, domain, IP, and token is fictional — synthetic exercise data modelled on public
2025–2026 AI-security incidents. No real credentials or indicators.

---

### Facilitators
The answer key, scoring cheat-sheet, and attack-path diagram are distributed **separately** and are
**not** in this repository — publishing them here would hand participants the solution.
