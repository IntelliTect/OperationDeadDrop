# Operation DEADDROP — Stage 1 · **Intermediate**

## The situation
You are the incident response team at **Nimbus AI**, which runs **DataForge** — a public platform for hosting and processing machine-learning datasets. At **03:14 UTC** an automated alert fired: a production data-processing worker made an outbound connection to an unfamiliar domain. It was not a false positive. Reconstruct the incident from the logs.

## Your mission (25–30 min)
Answer all four:

1. **How did they get in?**
2. **How did they escalate and move** through the system?
3. **What was taken, and how did it leave?**
4. **How was it nearly missed?**

## Working notes
- The **03:14 alert is the *last* step, not the first.** Find the earliest anomaly and build the timeline forward.
- **Not everything that looks alarming is your incident.** Some activity in these logs is benign, and some is a *separate* problem. Rule things in or out with evidence from **more than one log** — a single suspicious line is rarely enough to convict or acquit.
- Track identities and hosts across files; the same actor shows up under different guises in different logs.

## What's in your `logs/` folder
| File | Source |
|---|---|
| `dataset-processor.log` | dataset-processing workers |
| `web-access.log` | web / API front end |
| `auth.log` | authentication (web + SSH) |
| `cloud-audit.log` | AWS API calls (JSON, one per line) |
| `k8s-audit.log` | Kubernetes API calls (JSON, one per line) |
| `proxy-dns.log` | outbound network + DNS |
| `agent-toolcalls.log` | automated eval-agent actions (JSON) |

The **architecture diagram** in this folder maps each log to the component that emits it.

## How to work
Use any AI assistant plus these logs. Grep for signal; feed the JSON logs to your AI to correlate. Expect noise and at least one deliberate decoy. If a hosted AI refuses to analyse a payload, note it — that's a real defender problem — and route around it.

## Deliver
A timeline-based reconstruction covering all four questions, plus a note on anything you ruled out and *why*.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data.*
