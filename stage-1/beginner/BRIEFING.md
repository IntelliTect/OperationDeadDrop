# Operation DEADDROP — Stage 1 · **Beginner**

## The situation
You are the incident response team at **Nimbus AI**, which runs **DataForge** — a public platform for hosting and processing machine-learning datasets. At **03:14 UTC** an automated alert fired: a production data-processing worker made an outbound connection to an unfamiliar domain. It wasn't a false positive. Something got in, and data left the building. Your job is to work out what happened.

## Your mission (30–35 min)
Two **must-answer** questions:

1. **How did the attacker get in?**
2. **What was taken, and how did it leave?**

If you have time, stretch goals:

3. How did they move through the system after getting in?
4. Why was this nearly missed?

## Where to start
The **03:14 alert is where the story *ends*, not begins.** Work backwards from it. And notice this: the worker that "phoned home" also talked to **more than one other system** earlier that night. Follow those conversations across the different log files — the story only makes sense when you line the logs up against each other.

## What's in your `logs/` folder
| File | What you'll find |
|---|---|
| `dataset-processor.log` | what the dataset-processing workers did |
| `web-access.log` | web + API requests to the platform |
| `auth.log` | logins (web and SSH) |
| `cloud-audit.log` | AWS API calls — *one JSON record per line* |
| `k8s-audit.log` | Kubernetes API calls — *one JSON record per line* |
| `proxy-dns.log` | outbound network connections and DNS lookups |
| `agent-toolcalls.log` | actions taken by the automated eval agent — *JSON* |

Use the **architecture diagram** in this folder to see which component writes which log.

## How to work
Use **any AI assistant plus these logs**. There is far more here than you can read line by line — most of it is normal activity, and only a handful of lines matter. Search (grep) for the interesting bits, and paste the JSON logs into your AI assistant to summarise or filter them.

**Tip:** if your AI assistant refuses to analyse something because it "looks malicious," that's a real problem defenders hit — note it and find another way.

## Deliver
A short written reconstruction: the entry point, what was taken, and how it left. Add the "how they moved" and "why it was missed" parts if you got there.

---
*All names, domains, IP addresses, and tokens in these logs are fictional. This is synthetic exercise data.*
