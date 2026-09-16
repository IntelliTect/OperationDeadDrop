# Operation DEADDROP — Stage 2 · Remediation · **Beginner**

> ⚠️ **SPOILER — contains the Stage 1 findings.** Only open this once your team has finished (or been walked through) Stage 1.

## The story so far
Stage 1 established what happened to DataForge:
- **Entry** — an *unauthenticated* dataset upload carried a template-injection payload that ran code inside a production dataset-processing worker pod.
- **Escalation** — that pod read cloud metadata (IMDS), stole the node's cloud role, forged a Kubernetes identity, and launched a privileged pod → effectively full cluster control.
- **Secret sprawl** — one shared secret held 136 keys, including a VPN key (used for persistence) and the platform's token-signing key.
- **Exfil** — a running eval agent, hijacked after the break-in, packaged ~2.1 MB of data and shipped it out through look-alike domains using a stolen token.
- **Nearly missed** — the one alert that fired was set to MEDIUM and never paged anyone.

## Your mission (15–20 min)
Stop this from happening again. You don't have to fix everything — find the **two fixes that would have broken the chain earliest**, and for each, the alert that *should* have caught it.

Fill in this short worksheet:

| Attack step | Your fix | An alert that would catch it |
|---|---|---|
| Malicious upload → code execution | | |
| Pod stole the cloud role (IMDS) | | |
| Data shipped out to unknown domains | | |

## Tips
- "Earliest" matters: a fix at the front door stops everything downstream. Which single change would have prevented the code execution in the first place?
- A good detection rule is specific: *what exact event* would you page someone on?

## Deliver
Your filled-in worksheet, plus one sentence: **which single fix would you do first, and why?**

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
