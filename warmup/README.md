# Operation DEADDROP — Warm-up · The BCC Mystery

*An optional ~15-minute opener. No prior context needed — a good place to start if you arrive
early, before the main exercise begins.*

## The situation
A developer at **Nimbus AI** installed a handy open-source **MCP email connector** so their AI
agent could send notifications (password resets, invoices, alerts). This week a customer
complained that their password-reset email "somehow ended up somewhere else."

You've been handed two files. Find the problem.

## Your mission (~15 min)
Using only the two files in `logs/`, work out:

1. **How is data leaking** — what's the exfiltration channel?
2. **What caused it** — the exact change that introduced it?

## What's in `logs/`
| File | What it is |
|---|---|
| `mail-relay.log` | the mail server's outbound send log |
| `package-changelog.txt` | the email connector's version history |

## How to work
Use any AI assistant plus the two files. Most of the mail log is ordinary traffic — look for
anything that shouldn't be there, and line it up against the connector's version history. The two
files only make sense together.

## Deliver
Two things: **the exfiltration channel**, and **the exact change (which version) that introduced
it.**

## Why this matters
AI connectors and MCP servers often run with broad permissions and are trusted like any other
dependency — so a small, innocuous-looking package update can quietly become a data-exfiltration
channel. That's a supply-chain problem, and it's the mindset the main exercise builds on.

---
*All names, domains, IPs, and tokens are fictional. Synthetic exercise data modelled on a real
2025 incident.*
