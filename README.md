# Operation DEADDROP — Cyber Security & AI Tabletop

An interactive incident-response exercise. You play the IR team at **Nimbus AI**, whose
**DataForge** dataset platform has suffered a data-exfiltration breach. Using an AI assistant
and a bundle of realistic (synthetic) logs, you reconstruct **how the attacker got in, how they
moved, what they took, and why it was nearly missed** — and then decide what to do about it.

Bring a laptop and any AI chat assistant. Everything works offline against the files here.

## How the exercise unfolds

The exercise opens with a short **warm-up**, then runs in **three stages**. Each stage is
released to this repo's `main` branch as the session reaches it, so **don't be surprised if only
some of the folders below exist yet** — that is deliberate. Pull (or refresh the page) when the
facilitator announces a new stage.

| Part | Folder | Status |
|---|---|---|
| Warm-up | [`warmup/`](warmup/) | Available — start here if you arrive early |
| Stage 1 | [`stage-1/`](stage-1/) | Available |
| Stage 2 | [`stage-2/`](stage-2/) | Available |
| Stage 3 | [`stage-3/`](stage-3/) | Available |

The warm-up is optional and self-contained. The three stages build on each other, so keep your
notes from each stage — later stages start from what you produced earlier.

## Folder structure

The **warm-up** is one small folder for everyone, with no difficulty levels:

```
warmup/
├── README.md                     ← start here
└── logs/                         ← the evidence
```

Every **stage** folder follows the same layout, with one subfolder per difficulty level:

```
stage-N/
├── README.md                     ← start here: the stage overview and level chooser
├── beginner/
│   ├── BRIEFING.md               ← your level's mission
│   ├── logs/                     ← the evidence (where the stage uses logs)
│   └── architecture-diagram.png / .svg
├── intermediate/
│   └── (same layout)
└── advanced/
    └── (same layout)
```

- **`README.md`** (per stage) — the situation, what the stage is for, and a table to help you
  pick a level.
- **`BRIEFING.md`** (per level) — your mission for that stage, what to deliver, and a description
  of any files in that level's folder.
- **`logs/`** and **architecture diagrams** — the evidence bundle and a reference map of which
  component writes which log. Not every stage is a log-analysis stage, so some levels may have
  only a briefing.

## Choose your level

Pick **one** level per stage, based on your comfort with security investigations and how
powerful of an AI assistant you will be working with. Teams should keep the same level from
stage to stage, since each stage starts from the previous one's output.

| Level | Who it's for | What's different |
|---|---|---|
| `beginner/` | New to log analysis / mixed teams | Fewer must-answer questions, a starting nudge in the briefing, and a scaffolded diagram. Some background noise has been pre-triaged out. |
| `intermediate/` | Security-adjacent | All questions. Some background noise pre-triaged out. Neutral diagram. |
| `advanced/` | SOC / IR practitioners | The complete dataset — nothing pre-cleared. All questions plus decoy-clearing and incident scoping. |

Open the stage's **`README.md`**, then your level's **`BRIEFING.md`**.

## How to work
- The logs are noisy on purpose. Most lines are normal activity; a handful tell the story.
- Some files are **JSON, one record per line** (the briefing tells you which) — grep them, or
  paste them into your AI assistant to filter and summarise.
- Use the **architecture diagram** to see which component writes which log.
- If your AI assistant refuses to analyse something because it looks malicious, that's a real
  problem defenders face — note it and route around it.

## A note on the data
Every name, domain, IP address, and token in these logs is **fictional**. This is synthetic
exercise data modelled on public 2025–2026 AI-security incidents. It contains no real
credentials or indicators.

---

### Facilitators
The **answer keys**, **scoring cheat-sheets**, and **attack-path diagrams** for the warm-up and
every stage are distributed **separately** and are **not** in this repository — publishing them
here would hand participants the solution. Keep `FACILITATOR-NOTES.md`,
`README-FACILITATOR.md` and `FACILITATOR-CHEATSHEET.md` out of any public repo. Later stages
recap earlier answers, so release each stage only when the previous one has wrapped.
