# Operation DEADDROP — Stage 3 · Post-mortem

> ⚠️ **Stage 3 gives away Stages 1 & 2.** These materials recap the breach and its fixes, because
> the write-up starts from them. Only open this once your team has completed Stages 1 and 2.

You found the breach (Stage 1) and designed the fixes (Stage 2). **Stage 3 is where you write it
up** — a *blameless* post-mortem the company could publish. You'll draft it with an AI assistant
and then **verify its work**, which is the real skill here.

## The story so far
- **Root cause** — an unauthenticated dataset upload carried a template-injection payload → code execution in a worker pod.
- **Blast radius** — IMDS credential theft → forged Kubernetes identity → privileged pod → cluster-admin; a 136-key shared secret (incl. VPN + token-signing keys); ~2.1 MB / 5 eval datasets exfiltrated by a hijacked eval agent.
- **Detection gap** — the one correlated alert fired MEDIUM and never paged.
- **Stage 2** — your team proposed the remediation.

## Choose your level
Use the **same level your team ran in Stages 1 & 2.**

| Level | Scope | Time |
|---|---|---|
| [`beginner/`](beginner/) | A one-page blameless post-mortem | 20 min |
| [`intermediate/`](intermediate/) | Full post-mortem template + peer review of another team | 25 min |
| [`advanced/`](advanced/) | Full post-mortem + framework mapping + the *unresolved* hijacked-vs-driven question | 25 min + stretch |

Open your level's **`BRIEFING.md`** to start.

## How to work
- **Draft with any AI assistant, then read it back and verify** every claim against your own
  evidence. Drafting is the easy part; checking is the point.
- Two failure modes to catch in your AI's draft:
  1. a **hallucinated CVE or attribution** the logs don't support — cut it;
  2. **accidental individual blame** — "blameless" means systems and controls, not people.
- Don't state as fact anything the evidence only implies. Where the logs genuinely don't settle a
  question, **say so** and note what evidence *would* settle it — that's the stronger answer.

## What you'll produce
A blameless post-mortem the company could publish. Intermediate and advanced teams also
peer-review another team's against a short rubric.

## A note on the data
Every name, domain, IP, and token is fictional — synthetic exercise data.

---

### Facilitators
Release this only when Stage 2 wraps, and **don't commit it next to the Stage 1 logs** — the recap
above spoils the discovery puzzle. The model post-mortem / answer key is distributed separately.
The scoring rubric (including the +2/−1 for handling the hijacked-vs-driven question) is in
`FACILITATOR-CHEATSHEET.md`.
