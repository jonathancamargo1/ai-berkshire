---
name: financial-data
description: "AI Berkshire skill: Financial Data Sourcing & Cross-Validation Standard. Source: skills/financial-data.md."
---

## Codex adapter note

This skill is generated from `skills/financial-data.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Financial Data Sourcing & Cross-Validation Standard

This standard applies to all research involving corporate financial data. **Every key data point must come from two independent sources, variance >1% must be flagged.**

---

## Data Source Priority

### US Stocks (PDD, Tencent ADR, NetEase ADR, etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **macrotrends** | macrotrends.net/stocks/charts/{ticker} | Direct access, no registration required |
| 2 (Secondary) | **stockanalysis** | stockanalysis.com/stocks/{ticker}/financials | Direct access, no registration required |
| Primary Original | SEC EDGAR | sec.gov/cgi-bin/browse-edgar | Original 10-K / 10-Q text |

### Hong Kong Stocks (Tencent 0700, NetEase 9999, Meituan 3690, etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **aastocks** | aastocks.com/tc/stocks/analysis/company-fundamental | Direct access |
| 2 (Secondary) | **macrotrends** (ADR code) | Tencent use TCEHY, NetEase use NTES | Direct access |
| Primary Original | HKEX Disclosure | hkexnews.hk | Annual report PDF |

### China A-shares (37 Interaction, Gibit, etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **Eastmoney** | eastmoney.com → search stock code → financials table | Direct access |
| 2 (Secondary) | **CNINFO** | cninfo.com.cn | Original annual/quarterly report PDF |

---

## Execution Standard

### Step One: Obtain Data

For each financial metric (revenue, net profit, gross margin, operating cash flow, debt ratio, etc.), separately retrieve from **source 1** and **source 2**.

### Step Two: Variance Calculation & Flagging

```
Variance rate = |Source 1 value - Source 2 value| / Source 1 value × 100%
```

| Variance | Treatment Method |
|------|----------|
| ≤ 1% | ✅ Consistent, use source 1 value, note both sources |
| 1% ~ 5% | ⚠️ Flag "data has variance", note both values, explain possible cause (FX / accounting method) |
| > 5% | ❌ Flag "data has material variance", MUST verify original financial statements, cannot use directly |

### Step Three: Data Presentation Format

Every key data point must be annotated in format below:

```
Revenue: 123.9 billion yuan ✅
  - macrotrends: 124.1 billion yuan
  - stockanalysis: 123.7 billion yuan
  - Variance: 0.3%
```

Variance example:
```
Net Profit: 24.5 billion yuan ⚠️ Data has variance
  - macrotrends: 24.5 billion yuan (GAAP)
  - stockanalysis: 27.8 billion yuan (Non-GAAP)
  - Variance: 13.5% — Reason: Different accounting methodology (GAAP vs Non-GAAP)
```

---

## Common Variance Reasons (Not Necessarily Data Error)

| Reason | Explanation |
|------|------|
| GAAP vs Non-GAAP | Most common, especially for profit figures |
| Currency conversion | Different timing of CNY/HKD/USD conversion |
| Fiscal year definition | Calendar year vs fiscal year (e.g., Apple fiscal year ends October) |
| Consolidation methodology | Whether includes minority shareholder rights |
| Data update lag | Platform hasn't yet updated latest financial period |

---

## Special Rules

1. **Unlisted companies** (miHoYo, Lilith, etc.): When only one primary data source exists, flag data with `[Estimated]`, skip cross-validation
2. **Quarterly vs annual data**: Prefer annual data for cross-validation, quarterly in some sources may lag
3. **Original financial statement takes priority**: If both sources differ from original statement (10-K/annual report PDF), use original as standard, flag source error

---

## Quick Reference

| Scenario | Primary Source | Backup Source |
|------|---------|----------|
| PDD / Pinduoduo | macrotrends.net/stocks/charts/PDD | stockanalysis.com/stocks/pdd |
| Tencent | macrotrends.net/stocks/charts/TCEHY | aastocks (0700.HK) |
| NetEase | macrotrends.net/stocks/charts/NTES | aastocks (9999.HK) |
| 37 Interaction | eastmoney.com (002555) | cninfo.com.cn |
| Gibit | eastmoney.com (603444) | cninfo.com.cn |
| Nintendo | macrotrends.net/stocks/charts/NTDOY | stockanalysis.com/stocks/ntdoy |
| Capcom | macrotrends (CCOEY) | stockanalysis (CCOEY) |