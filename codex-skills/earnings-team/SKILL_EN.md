---
name: earnings-team
description: "AI Berkshire skill: Earnings Report Reading Team: Four Masters in Parallel + Public Account Publishing. Source: skills/earnings-team.md."
---

## Codex Adapter Note

This skill is generated from `skills/earnings-team.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`
- Before starting research, run the `date` command to confirm today's date.

# Earnings Report Reading Team: Four Masters in Parallel + Public Account Publishing

Perform team-based earnings report analysis for `$ARGUMENTS`. Four masters read earnings reports in parallel, editorial polishing creates content, reader reviewers ensure quality, final output produces directly publishable public account articles.

**Supported input formats**: `company name quarter`, for example: `Tencent 2025Q4`, `PDD 2025 Annual Report`, `Meituan Latest`

## Design Philosophy

A good earnings analysis solves two problems:
1. **You yourself understand the future** — requires deep research with four different perspectives
2. **Readers understand the value** — requires editorial polishing and reader perspective quality control

This Skill's workflow is divided into three phases:
- **Phase 1·Research**: Four masters read earnings reports carefully in parallel (Duan Yongping sees business essence, Buffett audits financial quality, Munger reads competitive changes, Li Lu hunts risk signals)
- **Phase 2·Synthesis**: Team Lead synthesizes four perspectives, produces research report draft
- **Phase 3·Publication**: Editor Agent rewrites as public account article + Reader Review Agent presents modification suggestions → Team Lead final draft