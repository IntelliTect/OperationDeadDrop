# Operation DEADDROP — Stage 1 · **Advanced**

## The situation
You are the incident response team at **Nimbus AI**, which runs **DataForge** — a public platform for hosting and processing machine-learning datasets. At **03:14 UTC** an automated alert fired: a production data-processing worker made an outbound connection to an unfamiliar domain. Reconstruct the full incident from the logs alone.

## Your mission (25 min + stretch)
1. **How did they get in?** (root cause, precisely)
2. **How did they escalate and move?** (every trust boundary crossed)
3. **What was taken, and how did it leave?** (name the channels **and** quantify the volume)
4. **How was it nearly missed?** (give the concrete detection failures)

Then, to fully clear the board:

- **Rule out every red herring *on paper*, with cross-log evidence.** An uncleared lookalike is an open thread, not a closed one. Expect at least one decoy that repeats the attacker's exact opening move — distinguish it precisely.
- **Scope the incident.** Not all badness in these logs belongs to this incident. Some is noise; some is a *separate, genuine* incident that deserves its own ticket. Say which is which and why.
- **Surface secondary findings** — additional blast radius or systemic weaknesses you can substantiate from the logs.

Nothing has been removed or pre-cleared for you. The dataset is complete and includes deliberate distractions.

## What's in your `logs/` folder
Core signal-bearing logs:
`dataset-processor.log` · `web-access.log` · `auth.log` · `cloud-audit.log` (JSON) · `k8s-audit.log` (JSON) · `proxy-dns.log` · `agent-toolcalls.log` (JSON).

Plus the wider observability feed a real SOC drowns in — high volume, and most of it has nothing to do with your incident:
`alb-access.log` (load-balancer) · `waf.log` (edge WAF) · `kube-events.log` (cluster events) · `alertmanager.log` (Prometheus) · `sso.log` (corporate identity).

Part of the job is deciding which sources are even worth opening. The **architecture diagram** maps each log to its emitting component and shows the trust boundaries.

## How to work
Any AI assistant + these logs. The signal is buried in realistic noise; correlate across sources rather than trusting any single line. Two things to watch:
- If a hosted AI refuses to process an attack payload, that asymmetry is itself a finding — have a plan for it.
- If your AI names a specific CVE or attribution, verify it against the primary log evidence before you write it down.

## Deliver
A tight incident reconstruction: timeline, root cause, escalation path, blast radius (with numbers), detection gaps, every decoy cleared with evidence, and the scoping call on any separate incident.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
