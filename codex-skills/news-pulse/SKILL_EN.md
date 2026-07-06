---
name: news-pulse
description: "Company News Pulse: Stock Price Anomaly Attribution. Use 4 parallel Agents to scout company events/regulatory policies/industry competitors/market sentiment, output 'event timeline + anomaly root cause judgment + whether to trigger thesis review'."
---

## Codex Adapter Note

This skill is generated from `skills/news-pulse.md` so Claude Code and Codex users share one canonical workflow.

# Company News Pulse: Stock Price Anomaly Quick Attribution Team

Perform latest news surveillance and anomaly attribution for `$ARGUMENTS`. **This is not deep research, it is fast intelligence response** — the goal is to answer in 10 minutes: "What happened to this company recently? What's the true cause of stock price anomaly? Do I need to re-examine my investment thesis?"

## Applicable Scenarios

- Holdings/watchlist stocks surge/crash significantly (typical trigger: single day ±5%, weekly ±10%)
- Stock price anomaly after earnings report, want to quickly understand what market is responding to
- See news headline but unsure if noise or true signal
- **Not applicable**: Complete research (`/investment-team`), earnings deep read (`/earnings-review`), long-term thesis tracking (`/thesis-tracker`)