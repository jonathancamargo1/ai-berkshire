# CLAUDE.md - AI Berkshire Project Instructions and Architecture

## Project Overview

Collection of value investment research Skills based on Claude Code. Four Masters Framework: Buffett, Munger, Tan Yongping, Li Lu.

**GitHub**: https://github.com/xbtlin/ai-berkshire

## Project Structure

```
skills/          — Investment research Skill definitions (.md)
tools/           — Auxiliary tools (financial_rigor.py precise calculation)
reports/         — Investment research report outputs
assets/          — Static resources such as images
codex-skills/    — Codex Skills definitions
codex-prompts/   — Codex Prompts library
```

## Reports Directory Structure

All reports are organized in folders by **company name**, with all related reports placed in the corresponding folder.

## Core Principles of Investment Research Analysis (Highest Priority)

- **Objective, objective, objective** — All investment research analysis must be based on facts and data, strictly prohibiting subjective speculation
- Rigorous distinction between "facts" and "opinions": facts are supported by data, opinions must be clearly marked
- **Do not predetermine position**: do not assume bullish or bearish bias, present data first, then deduce logic, finally reach conclusions
- Prohibited from using subjective expressions such as "I think", "in my opinion", etc.
- **Present both sides**: every central judgment must be accompanied by counter-evidence
- Be honest about uncertainties, say "uncertain" or "insufficient data", do not fill in with speculation

## GitHub Operations

- Local clone path: `~/ai-berkshire/`
- Remote repository: `https://github.com/xbtlin/ai-berkshire.git`
- Before pushing, run `git pull --rebase origin main`
- Commit messages in Chinese, clearly describing what was changed