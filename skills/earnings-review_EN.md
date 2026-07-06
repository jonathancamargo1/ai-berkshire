# Earnings Review: Deep-Read of Primary Data

Perform earnings analysis deep-read for $ARGUMENTS.

**Supported input formats**: `Company name Period`, for example: `Tencent 2025Q4`, `PDD 2025 Annual`, `Meituan Latest` (default: most recent period)

> "I never read sell-side research, only original financial reports." —— Li Lu
>
> "I read 500 pages per day. That's how knowledge accumulates, like compound interest." —— Warren Buffett

## Design Philosophy

Most AI investment research tools rely on secondary information (news, research summaries, data websites). But the core competency of Buffett and Li Lu is **reading primary sources** - annual reports, quarterly reports, call transcripts.

Problems with secondary information:
- Filtered - analysts selectively present data supporting their view
- Lagged - by the time others digest it, the alpha is gone
- Lacks context - "15% revenue growth" stripped of CEO's discussion of growth quality

This Skill reads primary materials directly, focusing on what Buffett and Li Lu actually examine.

## Execution Flow

### Preliminary Step: Data Availability Classification

| Level | Characteristics | Impact |
|------|------|------|
| Level A | Access to complete text (10-K/Annual/Call transcripts) | Execute all steps normally |
| Level B | Only partial text or third-party summaries | Mark "non-original source", reduce weight of supplementary analysis |
| Level C | Only news and website summaries | Focus on primary financial changes, skip supplementary analysis, mark "primary data insufficient" |

### First Step: Obtain Primary Data

Use Task tool to launch multiple Agents **in parallel** obtaining original materials:

1. **Original Financial Report**: From company IR pages, SEC EDGAR (10-K/10-Q for US), HKExnews (Hong Kong), Juchai.com.cn (China A-shares)
2. **Call Transcripts/Recordings**: From Seeking Alpha, company IR pages, Snowball etc.
3. **Management Letter to Shareholders** (if annual): Complete read
4. **Investor Day/Analyst Day Materials** (if recent): When available

If unable to get complete text, follow standards in `skills/financial-data.md` using standard sources (US: macrotrends+stockanalysis; Hong Kong: aastocks+macrotrends; China: Eastmoney+Juchai), but mark "not original report, third-party aggregation", and data with >1% difference between sources must be flagged.

### Second Step: Extract and Verify Core Financial Data

#### 2.1 Income Statement and Profits

| Indicator | Current Period | Prior Period | YoY Change | Management Guidance | On Target |
|------|------|------|---------|-----------|----------|

Must cover:
- Total revenue and breakdown by business/geography
- Gross profit, gross margin changes
- Operating profit, operating margin changes (GAAP vs Non-GAAP)
- Net profit (note: impact of non-recurring items)
- EPS (basic vs diluted)

#### 2.2 Cash Flow (what Buffett focuses on most)

| Indicator | Current Period | Prior Period | Change | Key Point |
|------|------|------|------|----------|

Must cover:
- Operating cash flow vs net profit: ratio >100% is good, <80% needs warning
- Capital expenditure and composition (maintenance vs expansion)
- Free cash flow = Operating cash flow - Capital expenditure
- Share buybacks, dividends
- Ending cash and equivalents balance

#### 2.3 Balance Sheet Health

Must cover:
- Cash + Short-term investments vs Interest-bearing liabilities
- Net cash/net debt trend
- Days sales outstanding (loosening credit to drive revenue?)
- Days inventory outstanding (buildup?)
- Goodwill and intangible assets (impairment risk?)

**Data Verification**: Use `tools/financial_rigor.py` to validate key data:

```bash
# Cross-validate revenue and net profit
python3 tools/financial_rigor.py cross-validate \
  --metric "revenue" --values 108.3e9 107.9e9 --sources "Company Report" "Yahoo Finance"

# Verify market cap
python3 tools/financial_rigor.py verify-market-cap \
  --price 101 --shares 1.488e9 --reported 1.44e11 --currency USD

# Calculate valuation metrics
python3 tools/financial_rigor.py verify-valuation \
  --price 101 --eps 9.6 --bvps 26.5 --fcf-per-share 10.2
```

### Third Step: Deep Read Management Discussion (MD&A)

This is where Buffett and Li Lu spend most time. Not about numbers, but about **how management speaks**.

#### 3.1 Management Tone Analysis

Read MD&A/call remarks paragraph by paragraph, marking:

| Signal Type | Specific Manifestation | Example |
|---------|---------|------|
| 🟢 **Honesty Signal** | Proactively acknowledge issues, provide specific reasons | "Our profit margin declined this quarter primarily because our investment in domain X exceeded expectations" |
| 🟢 **Clear Signal** | Strategy stated concretely with quantified targets | "We plan to increase market share in domain X from 15% to 20% over the next 12 months" |
| 🔴 **Vague Signal** | Heavy use of "we believe", "long-term" without substance | "We are optimistic about the future" |
| 🔴 **Deflection Signal** | Avoid direct questions, shift to other topics | Asked about margins, pivots to revenue growth |
| 🔴 **Externalize Blame** | Blame everything on macro/industry/competitors | "Due to macro environment..." |

#### 3.2 Commitment Tracking

Extract specific commitments from prior call/report, compare with current situation:

| Prior Commitment | Current Fulfillment | Assessment |
|---------|------------|------|
| "H2 profit margin will be X%" | Actual Y% | ✅On Track / ❌Missed / ⚠️Partially Met |

**Duan Yongping**: "The simplest way to judge if management is trustworthy is to see if they delivered on what they said before."

#### 3.3 Key Question Identification

Extract sharpest analyst questions, assess management response quality:

| Analyst Question | Management Response | Quality(1-5) | Dodged? |
|-----------|-----------|:--------:|:-----:|

### Fourth Step: Excavate Notes and Hidden Information

Report notes contain what management doesn't want you to easily find:

#### 4.1 Note Items to Check

- [ ] **Related Transactions**: Are transaction terms with shareholders/related parties fair?
- [ ] **Stock Incentives**: What is the dilution effect of options/RSUs? What is the strike price?
- [ ] **Contingent Liabilities**: Litigation, guarantees, off-balance commitments
- [ ] **Accounting Policy Changes**: Changes in revenue recognition, depreciation life?
- [ ] **Segment Information**: Margin differences across businesses - any good business subsidizing bad?
- [ ] **Customer/Supplier Concentration**: Top 5 customers/suppliers represent what percentage?

#### 4.2 Abnormal Signal Detection

- [ ] Receivables growth > revenue growth (stuffing channel?)
- [ ] Inventory growth > revenue growth (buildup?)
- [ ] Operating cash flow < net profit and gap widening (profit quality suspect?)
- [ ] Capital expenditure capitalization suddenly increases (prettifying profit?)
- [ ] Non-recurring income suddenly spikes

### Fifth Step: Compare with Historical Data

#### 5.1 Trend Analysis

Place key indicators in time series of at least 4 quarters (or 3 years of annuals):

| Indicator | Q-4 | Q-3 | Q-2 | Q-1 | Current Period | Trend Judgment |
|------|-----|-----|-----|-----|------|----------|

Key focus:
- Is profit margin improving or deteriorating?
- Is revenue growth accelerating or decelerating?
- Is cash flow quality improving or deteriorating?
- Is capital expenditure intensity increasing or decreasing?

#### 5.2 Compare with Management Guidance

| Indicator | Prior Management Guidance | Actual Result | Variance | Interpretation |
|------|--------------|---------|------|------|

### Sixth Step: Earnings Review Report Output

#### Report Structure

```
One, Core Data Overview (one-page table)
Two, Three Most Important Changes This Period (no more than 500 words)
Three, Management Tone and Commitment Tracking
Four, Hidden Information in Notes
Five, Key Questions (selected from call Q&A)
Six, Relationship to Investment Thesis (if applicable)
Seven, Conclusion: What Changed?
```

#### Conclusion Must Clearly Answer

1. **Is This Report Beats/Meets/Misses Expectations?** (cannot say "basically on track" then stay ambiguous)
2. **Impact on Investment Thesis**: Reinforces / No Impact / Weakens / Breaks
3. **What is the Next Catalyst to Watch?**
4. **If You Already Have Position, Should You Increase/Hold/Reduce?**

### Seventh Step: Save Report

Write report to `reports/{Company Name}-earnings-{Period}.md`, example `reports/Tencent-earnings-2025Q4.md`

### Eighth Step: Data Verification (Quality Check)

After writing report, execute data verification, only pass if approved:

```bash
# Step 1 — Extract verification checklist
python3 tools/report_audit.py extract \
  --report reports/{Company Name}-earnings-{Period}.md

# Step 2 — For each item, get data from reliable source (see skills/financial-data.md)

# Step 3 — Output approval/rejection verdict
python3 tools/report_audit.py verdict \
  --results '<filled JSON>' \
  --report {report filename}
```

**【APPROVED】** All passed → Publish; **【REJECTED】** Some failed → Fix and re-review.

## Key Principles

- **Read originals, not summaries**: Do everything to obtain primary data
- **Watch changes, not absolute values**: Trend matters more than numbers
- **Listen to tone, not just content**: How management speaks is as important as what they say
- **Check notes, not just body**: The devil is in the details
- **Give conclusions, not summaries**: The purpose of deep reading is forming judgment, not restating the report