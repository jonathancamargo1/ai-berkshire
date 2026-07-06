# AI Agents and Prompts Library

This repository contains multiple optimized Prompt templates and AI Agent definitions for use in Claude Code and Codex.

## Core Agents (19)

### Investment Research Category (7)

| Agent | Input | Output | Time |
|-------|-------|--------|------|
| `/investment-research` | Stock code | 12-dimensional structured report | 8-12 minutes |
| `/investment-team` | Stock code | Four Masters perspective + summary | 15-20 minutes |
| `/investment-checklist` | Stock code | 50-point checklist | 4-6 minutes |
| `/thesis-tracker` | Company ID | Continuous investment thesis tracking | Ongoing |
| `/earnings-review` | Earnings call transcript | Earnings analysis (expected vs actual) | 3-5 minutes |
| `/management-deep-dive` | Stock code | Management deep-dive analysis | 6-8 minutes |

And more...

## Codex Prompts

In the `codex-prompts/` directory, prompt templates are provided that can be used directly in Codex.

## How to Use

### In Claude Code

1. Install skills: `bash scripts/install-claude-commands.sh`
2. Use the command: `/investment-research PDD`

### In Codex

1. Copy the prompt from the `codex-prompts/` directory
2. Paste into Codex
3. Modify for the stock code you need

## Contributing a New Prompt

See CONTRIBUTING.md