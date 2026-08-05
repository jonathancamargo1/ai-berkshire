---
name: quality-screen
description: "AI Berkshire skill: Quality filter: 7 indicators to quickly eliminate non-first-class companies. Source: skills/quality-screen.md."
---

## Codex adapter note

This skill is generated from `skills/quality-screen.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Quality Filter: 7 Indicators to Quickly Eliminate Non-First-Class Companies

Execute quality indicator filter for $ARGUMENTS, quickly eliminating targets that don't meet first-class company standard.

**Supported input format**:

| Input Form | Example | Description |
|---------|------|----------|
| Individual stock | `Tencent, Meituan, NVIDIA` | Filter each one |
| Industry | `China beer industry` `Global cloud computing` `H-shares sports brands` | First search main listed companies of that industry (10-20), then filter each |
| Market/index | `Hang Seng constituents` `CSI 300` `NASDAQ 100` | Pull constituent list, filter each |
| Theme | `China high dividend 50` `Global AI compute chain` | First search theme-related companies, then filter each |

In industry/market/theme mode, output additionally contains: approval rate statistics, ranking within industry, sector comparison summary.

## Design Principle

- **Goal**: Don't wrongly eliminate any good first-class company, but can eliminate certain non-first-class companies
- **Logic**: 7 hard indicators + 2 exemption rules, better to let pass than wrongly eliminate
- **Applicability**: All listed companies (Bank/insurance doesn't apply condition 3 interest coverage)

---

## 7 Quality Filter Indicators

| # | Indicator | Elimination Condition | What It Measures |
|---|------|---------|----------|
| 1 | 10-year average ROE | < 8% | Capital efficiency —— can shareholder money beat opportunity cost? |
| 2 | 5-year cumulative free cash flow | Negative | Real gold —— is profit "paper wealth" or "real wealth"? |
| 3 | Interest coverage ratio (EBIT/interest) | < 2x | Repayment safety —— ability to pay interest |
| 4 | Long-term gross margin | < 15% | Pricing power —— does product/service have differentiation? |
| 5 | Operating cash flow / net profit (5-year average) | < 0.7 | Profit quality —— can earned profit collect cash? |
| 6 | Long-term net profit margin | < 5% | Risk resistance —— does profit go to zero when revenue fluctuates? |
| 7 | 5-year total share dilution | > 20% (non-M&A) | Shareholder interest —— is management diluting your rights? |

## 3 Exemption Rules

### Exemption A: Strategic investment period exemption (applies to #1)

If simultaneously satisfies 3 conditions, can exempt #1 insufficient ROE:
1. Listed less than 10 years
2. Gross margin > 30% (proves business model has pricing power)
3. Past 2 years operating cash flow positive (proves cash generation capability already established)

**Logic**: High gross margin + positive cash flow proves business model correct, low ROE just because still in investment period. Typical case: Meituan.

### Exemption B: Active low profit rate exemption (applies to #6)

If simultaneously satisfies 2 conditions, can exempt #6 insufficient net profit margin:
1. Gross margin > 30% (has ability to earn but chooses not to)
2. Past 2 years net profit margin already back above 5%, or clear increasing trend

**Logic**: High gross margin proves pricing power, low net profit margin is strategic choice (re-investment) not capability insufficiency. Typical case: Amazon.

### Exemption C: High-turnover thin-margin model exemption (applies to #4 and #6)

If simultaneously satisfies 3 conditions, can exempt #4 gross margin and #6 net profit margin insufficient:
1. ROE > 20% (proves though profit margin low, but capital return rate extremely high)
2. Operating cash flow/net profit > 1.0 (profit quality no problem)
3. Business model is "membership/platform commission/high-turnover thin-margin" type (profit not shown in gross margin)

**Logic**: Some first-class companies profit not in gross margin, but in membership fee, platform commission or turnover efficiency. Gross margin and net profit naturally low, but high ROE proves first-class capital efficiency. Typical case: Costco (12% gross margin, 2.5% net margin, but 25%+ ROE, 90%+ membership renewal rate).

---

## Execution Flow

### Step One: Analyze input, determine filter scope

**Mode judgment**:
- If input is specific company/code → **individual stock mode**, go directly to step two
- If input is industry/market/theme → **batch mode**, first execute operation:
  1. Use WebSearch to search main listed companies of that industry/market/theme
  2. Industry mode: cover top 15-20 listed companies of that industry
  3. Index mode: pull complete constituent list
  4. Theme mode: search related companies, cover 15-30 companies
  5. List complete company list for confirmation (if companies > 30, process in parallel batches)

For each company confirm full name, code, exchange.

### Step Two: Parallel data collection

For each company launch independent background Agent, use WebSearch to search following data:

1. **ROE**: Each year ROE of past 10 years (or since listing), calculate average
2. **Free cash flow**: Operating cash flow and capital expenditure past 5 years, calculate 5-year cumulative FCF
3. **Interest coverage**: Latest year EBIT and interest expense, calculate ratio
4. **Gross margin**: Gross margin trend past 5 years
5. **Operating cash flow/net profit**: Ratio of past 5 years, calculate average
6. **Net profit margin**: Net profit margin trend past 10 years, calculate average
7. **Total shares change**: Total shares 5 years ago vs current, calculate dilution proportion

Data source priority: Company annual report > Broker research > Financial data platform

### Step Three: Line-by-line verification

For each company, verify line by line 7 indicators:
- ✅ Passed
- ❌ Failed
- ⚠️ Boundary (attach value as description)

If violated certain line, check if satisfies corresponding exemption condition.

### Step Four: Output result

#### Output format

```markdown
# Quality Filter Result

**Filter date**: {today date}
**Company quantity**: {N} companies

## Summary Table

| Company | ①ROE | ②FCF | ③Interest coverage | ④Gross margin | ⑤OCF/NI | ⑥Net margin | ⑦Dilution | Result |
|------|------|------|----------|---------|---------|---------|-------|----------|
| xxx | ✅ 24% | ✅ | ✅ | ✅ 56% | ✅ | ✅ 30% | ✅ | **Passed** |
| yyy | ❌ 3% | ❌ | ❌ | ✅ 20% | ✅ | ❌ 2% | ✅ | **Eliminated** |
| zzz | ⚠️→✅ | ✅ | ✅ | ✅ 35% | ✅ | ⚠️→✅ | ✅ | **Exemption Passed** |

## Companies Passed (N companies)
[List]

## Companies Eliminated (N companies)
| Company | Violated Indicator | Specific Data | Elimination Reason |
|------|---------|---------|----------|

## Companies Exemption Passed (N companies)
| Company | Exemption Clause | Specific Data | Exemption Reason |
|------|---------|---------|----------|

## Boundary Controversy (if any)
[Additional explanation for companies near threshold]

## Sector Summary (industry/market mode specific)

**Pass rate**: {number passed}/{total} = {percentage}
**Industry quality judgment**: [per pass rate give overall industry quality assessment]

| Quality Stratification | Company | Common Traits |
|---------|------|----------|
| First-class (passed all+high ROE) | xxx, yyy | ... |
| Qualified (passed all but indicator mediocre) | aaa, bbb | ... |
| Eliminated | ccc, ddd | ... |

**Industry stock selection conclusion**: [one-sentence summary whether this industry worth digging deeper, which 2-3 companies most worth attention]
```

---

## Notes

1. **Bank/insurance**: Doesn't apply #3 (interest coverage), business model essence is interest spread operation
2. **REIT**: ROE may fluctuate greatly from property revaluation, use "core operating profit ROE" instead
3. **Insufficient data**: If certain data can't be obtained, mark "insufficient data" rather than directly judge pass/fail
4. **Cyclical industry**: Use complete cycle average (cover at least peak high and peak low), don't use single year
5. **Short listing time**: Less than 5 years company use all available data, but in result mark "data window insufficient"

## Limitation Statement

This indicator set can eliminate "definitely not good" companies, but passed filter not equal "definitely good". Passed companies still need further research:
- Is business model sustainable?
- Is management trustworthy?
- Is current valuation reasonable?
- Is competitive landscape deteriorating?

Quality filter is step one, not final step.