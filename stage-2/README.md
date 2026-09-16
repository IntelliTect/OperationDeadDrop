# Operation DEADDROP — Stage 2 · Remediation

> ⚠️ **Stage 2 gives away Stage 1.** These materials recap what the breach was, because
> remediation starts from the Stage 1 findings. Only open this once your team has completed
> (or been walked through) Stage 1.

In Stage 1 you reconstructed the DataForge breach. **Stage 2 is where you close the holes.**
For each step of the attack you'll design two things: a **fix** that stops it, and a
**detection / logging improvement** so it's caught faster next time.

## The story so far
- **Entry** — an *unauthenticated* dataset upload carried a template-injection payload that ran code inside a production dataset-processing worker pod.
- **Escalation** — that pod stole the node's cloud role via IMDS, forged a Kubernetes identity, and launched a privileged pod → effectively full cluster control.
- **Secret sprawl** — one shared secret held 136 keys, including a VPN key (used for persistence) and the platform's token-signing key.
- **Exfil** — a hijacked eval agent shipped ~2.1 MB (5 eval datasets) out through look-alike domains using a stolen write token.
- **Nearly missed** — the one correlated alert fired MEDIUM and never paged.

## Choose your level
Use the **same level your team ran in Stage 1.** Each folder holds a briefing for that tier.

| Level | Scope | Time |
|---|---|---|
| [`beginner/`](beginner/) | The two fixes that break the chain earliest, on a short worksheet | 15–20 min |
| [`intermediate/`](intermediate/) | Full attack-step → fix + detection worksheet; name the earliest choke point | 20–25 min |
| [`advanced/`](advanced/) | Full worksheet + systemic fixes + write a real detection rule | 25 min + stretch |

Open your level's **`BRIEFING.md`** to start.

## How to work
- Start from **your Stage 1 findings** — the attack chain you reconstructed is the input to this stage.
- For every fix, ask two questions: *is this at the right layer?* and *what exact event would I page someone on if it happened again?*
- Prevention and detection are both valid answers. Where prevention is uncertain, a sharp detection rule may be the stronger control.
- Use any AI assistant to help draft and pressure-test your fixes.

## What you'll produce
A remediation plan mapping each attack step to a fix **and** a detection improvement — plus, for
advanced teams, the systemic fixes (secret handling, least-privilege RBAC, eval/prod isolation,
egress control) and at least one written detection rule.

## A note on the data
Every name, domain, IP, and token is fictional — synthetic exercise data.

---

### Facilitators
Release this only when Stage 1 wraps, and **don't commit it next to the Stage 1 logs** — the
recap above spoils the discovery puzzle. The remediation model solution / answer key is
distributed separately.
