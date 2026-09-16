# Operation DEADDROP — Stage 3 · Post-mortem · **Intermediate**

> ⚠️ **SPOILER — contains the Stage 1 & 2 findings.** Only open this once your team has done Stages 1 and 2.

## The story so far
- **Root cause** — an unauthenticated dataset upload carried an SSTI payload → RCE in a worker pod.
- **Blast radius** — IMDS credential theft → forged Kubernetes node identity → privileged pod → cluster-admin; a 136-key shared secret (incl. VPN + JWT signing keys); ~2.1 MB / 5 eval datasets exfiltrated by a hijacked eval agent.
- **Detection gap** — a correlated alert fired MEDIUM and never paged.
- **Stage 2** — your team produced the remediation.

## Your mission (25 min)
Write a **blameless** post-mortem the company could publish, then peer-review another team's. Use your AI assistant to draft, then verify against your own evidence.

Template:

```
1. Executive summary — 3 sentences: what happened, impact, status.
2. Timeline (UTC) — the key events, in order.
3. Root cause — the initial access vector, stated plainly.
4. Escalation & blast radius — how far it spread; what data left.
5. Detection & the gap — how it was found, and why it was nearly missed.
6. Remediation — what was fixed (from Stage 2).
7. Lessons learned.
```

## Watch your AI's draft for
- **Hallucinated attribution** — a specific CVE or "threat group" the logs don't support. Cut it.
- **Accidental blame** — blameless means systems and controls, not individuals.
- **Overreach** — don't state as fact anything your evidence only implies.

## Peer review
Swap post-mortems with another team. Score theirs 1–3 on: accurate timeline, correct root cause, clear blast radius, honest (blameless) detection-gap, actionable remediation.

## Deliver
Your post-mortem + your peer-review scores for another team.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
