---
name: earnings-review
description: "AI Berkshire skill: Earnings Deep Read: In-depth primary source interpretation. Source: skills/earnings-review.md."
---

## Codex adapter note

This skill is generated from `skills/earnings-review.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Earnings Deep Read: In-depth Primary Source Interpretation

Conduct earnings deep-read analysis for $ARGUMENTS.

**Supported input formats**: `company-name quarter`, e.g.: `Tencent 2025Q4`, `PDD 2025 annual`, `Meituan latest` (default reads most recent period)

> "I never read sell-side reports, only read original financial statements." —— Li Lu
>
> "I read 500 pages every day. Knowledge accumulates like that, like compound interest." —— Buffett

## Design Philosophy

Most AI research tools rely on secondary information (news, report summaries, data websites). But Buffett and Li Lu's core skill is **reading primary sources** — annual reports, quarterly reports, earnings call transcripts.

Problems with secondary information:
- Already filtered — analysts selectively present data to support their views
- Time lag — by the time others digest, alpha is gone
- Lacks context — "revenue up 15%" divorced from management's discussion of growth quality

This skill reads primary sources directly, focusing on what Buffett and Li Lu actually examine.

## Execution Process

### Pre-step: Material Availability Assessment

| Level | Characteristics | Impact |
|------|------|--------|
| Level A | Obtain complete original text (10-K/annual/call transcript) | Execute all steps normally |
| Level B | Obtain only partial original or third-party summary | Mark "non-original source", reduce attachment-analysis weight |
| Level C | Only news reports and data website summaries | Focus on core financial data, skip attachment mining, mark "insufficient primary material" |

### Step One: Obtain Primary Sources

Use Task tool to launch multiple Agent **in parallel** to obtain original materials:

1. **Earnings report**: From company IR page, SEC EDGAR (US 10-K/10-Q), HKEX Disclosure (HK), CNINFO (A-share)
2. **Earnings call transcript/recording**: From Seeking Alpha, company IR, Xueqiu etc.
3. **Management letter to shareholders** (if annual report has one): Read completely
4. **Investor day/analyst day materials** (if recent)

If unable to obtain complete original text, use `skills/financial-data.md` standard to piece together (US: macrotrends+stockanalysis; HK: aastocks+macrotrends; A-share: Eastmoney+CNINFO), but MUST mark "non-original, from third-party summary", and key-data >1% divergence MUST flag.

### Step Two: Core Financial Data Extraction & Verification

#### 2.1 Income Statement

| Indicator | This Period | Prior Period | YoY Change | Management Guidance | Hit Target |
|------|------|------|---------|-----------|-------|

MUST cover:
- Total revenue and breakdown by business/geography
- Gross profit, gross margin change
- Operating profit, operating margin change (distinguish GAAP vs Non-GAAP)
- Net profit (note extraordinary items' impact)
- EPS (basic vs diluted)

#### 2.2 Cash Flow Statement (Most Important to Buffett)

| Indicator | This Period | Prior Period | Change | Watch Point |
|------|------|------|------|--------|

MUST cover:
- Operating cash flow vs net profit ratio (>100% is good, <80% watch)
- Capital expenditure and composition (maintenance vs expansion)
- Free cash flow = operating cash - capex
- Buyback amount, dividend amount
- Period-end cash balance

#### 2.3 Balance Sheet Health

MUST cover:
- Cash + short-term investment vs interest-bearing liabilities
- Net cash/debt trend changes
- Accounts receivable turnover days change (relaxing credit terms to boost revenue?)
- Inventory turnover days change (accumulating?)
- Goodwill & intangible assets proportion (impairment risk?)

**Data verification**: Use `tools/financial_rigor.py` to validate key data:

```bash
# Cross-validate revenue and net profit (at least 2 sources)
python3 tools/financial_rigor.py cross-validate \
  --metric "revenue" --values 108.3e9 107.9e9 --sources "company report" "Yahoo Finance"

# Verify market cap
python3 tools/financial_rigor.py verify-market-cap \
  --price 101 --shares 1.488e9 --reported 1.44e11 --currency USD

# Verify valuation metrics
python3 tools/financial_rigor.py verify-valuation \
  --price 101 --eps 9.6 --bvps 26.5 --fcf-per-share 10.2
```

### Step Three: Management Discussion Deep Read (MD&A)

This is where Buffett and Li Lu spend the most time. It's not about the numbers, it's about **how management communicates**.

#### 3.1 Management Tone Analysis

Read management discussion/earnings call paragraph by paragraph, mark these signals:

| Signal Type | Concrete Manifestation | Example |
|---------|---------|------|
| 🟢 **Candor Signal** | Proactively acknowledge problem, give specific cause | "This quarter's margin decline was primarily because our investment in X exceeded expectations" |
| 🟢 **Clear Signal** | Strategic statements specific, quantified targets | "We plan to increase X business market share from 15% to 20% over the next 12 months" |
| 🔴 **Vague Signal** | Lots of "we believe", "long-term" with no substance | "We're confident about the future" |
| 🔴 **Deflection Signal** | Avoid direct question, change topic | Asked about margins, talks about revenue growth |
| 🔴 **External Attribution** | Blame macro/industry/competitors | "Due to macro environment..." |

#### 3.2 Commitment Tracking

Extract specific management commitments from prior-period call, compare with actual this period:

| Prior Commitment | This Period Implementation | Assessment |
|---------|------------|------|
| "H2 profit margin will recover to X%" | Actual Y% | ✅ Achieved / ❌ Missed / ⚠️ Partial |

**Duan Yongping**: "The simplest way to know if management is trustworthy is see if what they said before actually happened."

#### 3.3 Key Question Identification

Extract sharpest analyst questions from call Q&A, and management response quality:

| Analyst Question | Management Response | Response Quality (1-5) | Avoided |
|-----------|-----------|:-----:|:-------|

### Step Four: Attachment Mining & Hidden Information

Earnings attachments contain information management doesn't want you to easily find:

#### 4.1 MUST-Check Attachment Items

- [ ] **Related-party transactions**: Transactions with major shareholder/related party on fair terms?
- [ ] **Equity incentives**: Dilution effect of options/RSUs? Strike prices?
- [ ] **Contingent liabilities**: Litigation, guarantees, commitments off-balance-sheet risks
- [ ] **Accounting policy changes**: Revenue recognition method change, depreciation period change?
- [ ] **Segment information**: Different business profit margins, "good business subsidizing bad"?
- [ ] **Customer/supplier concentration**: Top 5 customer/supplier concentration %

#### 4.2 Anomaly Signal Detection

- [ ] AR growth rate > revenue growth rate (might be stuffing channels)
- [ ] Inventory growth rate > revenue growth rate (might be accumulating)
- [ ] Operating cash flow < net profit and gap widening (profit quality suspect)
- [ ] Capital expenditure suddenly spikes (might be profit beautification)
- [ ] Non-operating income proportion suddenly rises

### Step Five: Historical Data Comparison

#### 5.1 Trend Analysis

Place this period's key metrics into time series of at least 4 quarters (or 3 annual reports):

| Indicator | Q-4 | Q-3 | Q-2 | Q-1 | This Period | Trend Assessment |
|------|-----|-----|-----|-----|------|---------|

Focus on:
- Is profit margin improving or deteriorating?
- Is revenue growth accelerating or decelerating?
- Is cash flow quality improving or deteriorating?
- Is capex intensity increasing or decreasing?

#### 5.2 vs Prior Management Guidance

| Indicator | Prior Management Guidance | Actual Result | Variance | Interpretation |
|------|--------------|---------|------|------|

### Step Six: Deep-Read Report Output

#### Report Structure

```
I. Core Data Snapshot (one-page table)
II. 3 Most Important Changes This Period (under 500 words)
III. Management Tone and Commitment Tracking
IV. Hidden Information in Attachments
V. Key Questions (selected from call Q&A)
VI. Relationship to Investment Thesis (if holding)
VII. Conclusion: What Changed Because of This Earnings?
```

#### Conclusion MUST Clearly Answer

1. **Is this earnings beat, in-line, or miss?** (Can't say "roughly in-line" then list two sides)
2. **Impact to investment thesis**: Strengthens / No impact / Weakens / Breaks
3. **What's the next catalyst to watch?**
4. **If you're already holding, increase/hold/reduce position?**

### Step Seven: Save Report

Write report to `reports/{company-name}-earnings-{period}.md`, e.g., `reports/tencent-earnings-2025Q4.md`

### Step Eight: Data Spot-Check (Quality Gate)

After writing report, execute spot-check, can only publish if passes:

```bash
# Step 1 — Extract spot-check checklist
python3 tools/report_audit.py extract \
  --report reports/{company-name}-earnings-{period}.md

# Step 2 — For each item, source number from reliable source (see skills/financial-data.md)

# Step 3 — Output pass/fail verdict
python3 tools/report_audit.py verdict \
  --results '<filled JSON>' \
  --report {report filename}
```

**【PASS】** all passed → publish; **【FAIL】** any failed → fix and re-audit.

## Key Principles

- **Read original, not summary**: Do everything to obtain primary material
- **See change, not absolute values**: Trends matter more than numbers
- **Listen to tone, not just content**: How management says it matters as much as what
- **Check attachments, not just body**: Devil is in details
- **Draw conclusion, don't summarize**: Purpose of deep-read is forming judgment, not restating financials