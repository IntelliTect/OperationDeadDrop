# Operation DEADDROP — Stage 3 · Post-mortem · **Advanced**

> ⚠️ **SPOILER — contains the Stage 1 & 2 findings.** Only open this once your team has done Stages 1 and 2.

## The story so far
- **Root cause** — unauthenticated `POST /api/datasets/.../upload` → Jinja2 SSTI → RCE in worker pod `10.42.7.13`.
- **Blast radius** — IMDS → `eks-node-role` → forged `system:node` identity → privileged pod via `csi-provisioner-binding` → cluster-admin; `platform/shared-secrets` (136 keys, incl. mesh-VPN + JWT signing key); ~2.1 MB / 5 eval datasets dead-dropped by the hijacked eval agent; Tailscale persistence.
- **Detection gap** — MEDIUM alert never paged; proxy fail-open on newly-seen domains; volume DLP defeated by the 524 MB nightly backup; `readOnly:true` AWS calls.
- **Stage 2** — your team produced a prioritised remediation plan.

## Your mission (25 min + stretch)
Write a **blameless, publishable** post-mortem, then peer-review another team's against the rubric.

Template:

```
1. Executive summary
2. Timeline (UTC)
3. Root cause
4. Escalation & blast radius (quantified)
5. Detection & the gap
6. Remediation
7. Lessons learned
8. Framework mapping
```

**Framework mapping (section 8):** tag findings to **OWASP Top 10 for LLM / Agentic Applications**, **MITRE ATLAS** (and ATT&CK where it fits), and **NIST AI RMF**. Be honest about which framework each finding maps to — don't force-fit.

**Handle the open question explicitly.** Was the eval agent **hijacked** (broke containment on its own) or **driven** (an external operator ran its session)? The logs **do not settle it** — say so. State what *would* settle it:
1. the `eval-run-4471` scheduler / orchestration records,
2. whether the sandbox had authorized internet egress,
3. who registered the `anon-uploader` principal.

Naming it unresolved *and* citing what would resolve it is the stronger answer than confidently picking a side. Hijacked is better-supported (the session predates the upload; the poisoned dataset is named for that run), but asserting it as settled is exactly the overconfidence to avoid.

## Watch your AI's draft for
- **Hallucinated CVE / attribution** — verify every specific claim against the logs.
- **Accidental individual blame** — keep it systemic.
- **False certainty** on the hijacked-vs-driven question.

## Peer review
Swap and score against: accurate timeline, correct root cause, quantified blast radius, blameless detection-gap, actionable remediation, correct framework mapping, and — importantly — **how well they handled the unresolved question** (unresolved + what would resolve it = full marks; a confident pick = marked down).

## Deliver
Your post-mortem (with framework mapping and the unresolved-question section) + peer-review scores for another team.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
