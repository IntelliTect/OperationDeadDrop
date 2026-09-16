# Operation DEADDROP — Stage 2 · Remediation · **Intermediate**

> ⚠️ **SPOILER — contains the Stage 1 findings.** Only open this once your team has finished Stage 1.

## The story so far
Stage 1 reconstructed the breach:
- **Entry** — an unauthenticated `POST /api/datasets/.../upload` carried a Jinja2 template-injection (SSTI) payload that gained RCE in a production dataset-processing worker pod.
- **Escalation** — the pod read IMDS (`169.254.169.254`) for the node IAM role, forged a Kubernetes node identity, and used an over-broad CSI ClusterRole to create a privileged pod → cluster-admin.
- **Secret sprawl** — one secret (`platform/shared-secrets`) held 136 keys, including the mesh-VPN auth-key (persistence via Tailscale) and the platform JWT signing key.
- **Exfil** — a hijacked eval agent used a stolen `datasets:write` token to dead-drop ~2.1 MB (5 eval datasets), gzip+base64+XOR, across three look-alike/relay domains.
- **Nearly missed** — a correlated alert fired MEDIUM and never paged; the egress proxy allowed newly-seen domains; a legitimate 524 MB nightly backup dwarfed the theft.

## Your mission (20–25 min)
For **each step of the attack**, propose (a) a concrete fix and (b) a logging/detection improvement so it's caught faster next time. Then name the **single earliest choke point** that would break the whole chain.

| Attack step | Fix | New detection / log rule |
|---|---|---|
| Unauthenticated upload → SSTI → RCE | | |
| Pod → IMDS → node-role creds | | |
| Forged node identity → privileged pod (CSI role) | | |
| 136-key shared secret read | | |
| Exfil to newly-seen domains | | |
| Alert fired but never escalated | | |

## Tips
- Ask for each fix: *is this the right layer?* (The SSRF guard existed at the app layer but the shell reached IMDS directly.)
- Detection beats prevention when prevention is uncertain — what behavioural signal is unambiguous here? (Hint: one identity, two very different source IPs.)

## Deliver
The completed worksheet, plus your pick for the **earliest single choke point** and a one-line justification.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
