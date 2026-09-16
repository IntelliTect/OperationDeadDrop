# Operation DEADDROP — Stage 3 · Post-mortem · **Beginner**

> ⚠️ **SPOILER — contains the Stage 1 & 2 findings.** Only open this once your team has done Stages 1 and 2.

## The story so far
- **What happened** — an unauthenticated dataset upload ran code on a DataForge worker, which stole cloud/cluster access and (via a hijacked eval agent) shipped ~2.1 MB of data out to unknown domains.
- **Why it nearly slipped by** — the one alert that fired was set to MEDIUM and never paged anyone.
- **Stage 2** — your team proposed the fixes.

## Your mission (20 min)
Write a short, **blameless** post-mortem the company could share internally — about one page. "Blameless" means you describe what the *systems* did, not who to blame. Use your AI assistant to draft it, then read it back and fix anything wrong.

Use this template:

```
INCIDENT POST-MORTEM — DataForge data exfiltration

1. Summary (3 sentences): what happened, what was taken, current status.
2. What went wrong (the root cause, in plain terms).
3. What was taken.
4. How we fixed it (from Stage 2).
5. One lesson we're taking away.
```

## Two things to check in your AI's draft
1. **Did it invent a "CVE" or a technical detail that isn't in your findings?** If so, cut it.
2. **Did it blame a person?** Rewrite to focus on the system that allowed it.

## Deliver
Your one-page post-mortem.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
