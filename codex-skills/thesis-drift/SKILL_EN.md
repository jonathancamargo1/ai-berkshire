---
name: thesis-drift
description: "AI Berkshire skill: Investment thesis drift detection: Distinguish fact change from wording change. Source: skills/thesis-drift.md."
---

## Codex adapter note

This skill is generated from `skills/thesis-drift.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Investment Thesis Drift Detection: Distinguish Fact Change from Wording Change

Execute investment thesis drift detection for $ARGUMENTS.

**Supported input format**:
- `company-name old-report-path new-report-path` — specify two research reports or thesis snapshots for comparison
- `company-name reports/{company-name}-thesis-old-date.md reports/{company-name}-thesis-new-date.md` — compare two dated thesis snapshots
- `company-name` — automatically find `reports/{company-name}-thesis.md` and historical snapshots in same directory; if no baseline convert to baseline-missing processing

> "When facts change, I change my mind. Do you?" —— Keynes
>
> "Stock price fluctuation is not thesis drift, changed facts are." —— AI Berkshire

## Design Philosophy

Holding long-term position is hardest not reading news daily, but distinguishing three things:
- **Fact changed**: Revenue, profit margin, competitive landscape, management behavior, capital allocation has verifiable change
- **Price changed**: Market emotion or valuation multiple changed, but business itself unchanged
- **Wording changed**: Two reports different writing form, but underlying evidence and judgment unchanged

Investment thesis drift detection goal is: **only when evidence changes admit thesis change**. Can't create false drift because report rewrote, also can't because stock price fluctuated wrongly misjudge fundamentals.

This Skill depends on `/thesis-tracker` output of structured dimensions: key assumption checklist, red-line checklist, valuation anchor, tracking record table. Without these structures, first complete baseline, then execute drift detection.

## Execution Flow

### Step One: Judge operation mode

Analyze `$ARGUMENTS`:
- If provided two report paths → enter **specified report comparison mode**
- If only provided company name → find `reports/{company-name}-thesis.md` and historical snapshots, enter **automatic snapshot comparison mode**
- If found only one report or no historical baseline → enter **missing baseline processing mode**
- If two reports not same company → stop and request user confirmation, don't do cross-company drift judgment

---

## Mode A: Specified Report Comparison

### A1: Read and validate two reports

Read old and new reports, extract:
- Report date, company name, stock code
- Core thesis (5 sentences)
- Key assumption checklist
- Red-line checklist
- Valuation anchor
- Tracking record table
- Management quality judgment
- Competitive moat judgment
- Current action recommendation (buy / hold / watch / reduce / exit)

If report missing key structure, first mark "structure missing", but still try to extract evidence from body; if can't extract dimension mark as "can't judge", can't fabricate conclusion.

### A2: Evidence normalization

Organize factual evidence from two reports into same table:

| Dimension | Old Report Evidence | New Report Evidence | Data Source | Can Verify? |
|------|-----------|-----------|---------|----------|
| Valuation anchor | | | | |
| Key assumption | | | | |
| Red-line | | | | |
| Management quality | | | | |
| Competitive moat | | | | |

**Only compare evidence, don't compare wording.** If new and old report only synonymous rewrite, order change, tone change, but factual data and judgment threshold unchanged, judge as Unchanged.

### A3: Value and valuation verification

All value changes must use `tools/financial_rigor.py` for exact calculation, LLM mental calculation prohibited:

```bash
python3 tools/financial_rigor.py verify-valuation \
  --price {current price} \
  --eps {EPS} \
  --bvps {book value per share} \
  --fcf-per-share {FCF per share}
```

If need calculate market cap, percentage change, target price difference or scenario valuation, use:

```bash
python3 tools/financial_rigor.py verify-market-cap --price {price} --shares {shares} --reported {reported market cap} --currency {currency}
python3 tools/financial_rigor.py cross-validate --field {field} --values '{JSON}' --unit {unit}
python3 tools/financial_rigor.py three-scenario --price {price} --eps {EPS} --shares {billions of shares} --growth {optimistic} {neutral} {pessimistic} --pe {optimistic PE} {neutral PE} {pessimistic PE}
python3 tools/financial_rigor.py calc --expr '{exact formula}'
```

Key financial data must cross-verify from at least two independent places. Insufficient source, inconsistent caliber, can't verify number must mark as "low confidence / awaiting verification".

### A4: Drift judgment by dimension

Use fixed following dimensions, don't add/reduce temporarily:

| Dimension | Judgment Focus | Improved | Unchanged | Weakened |
|------|---------|----------|-----------|----------|
| Valuation anchor | Intrinsic value, PE/PB/FCF Yield, safety margin, target price range | Safety margin expands or intrinsic value upgraded and tool-verified | Valuation range and safety margin no material change | Safety margin narrows, intrinsic value downgrades or valuation assumption fails |
| Key assumption checklist | Revenue growth, profit margin, cash flow, user/order/capacity etc verifiable assumption | More assumptions strengthened by new evidence | Assumption status consistent with evidence | Assumption weakened, damaged or broken |
| Red-line checklist | Integrity, regulation, business collapse, competition breakthrough, abnormal management action | Original red-line risk resolved or significantly decreased | Didn't trigger and risk level unchanged | Red-line triggered or trigger probability increased |
| Management quality | Integrity, capital allocation, buyback dividend, execution, shareholder friendliness | New behavior increases trust | Behavior continues old judgment | Behavior damages trust or capital allocation worsens |
| Competitive moat | Market share, pricing power, network effect, cost advantage, substitution threat | Moat widens or competitive advantage verified | Landscape no material change | Moat weakened or competitor breaks through |

Each dimension only three conclusion types: **Improved / Unchanged / Weakened**.

### A5: Evidence-driven rule

Each non-Unchanged conclusion must cite specific new evidence causing change:
- Financial line items: like revenue growth, profit margin, operating cash flow, buyback amount, net cash
- Regulatory disclosure: like 10-K/20-F, annual report, interim report, exchange announcement, SEC filing
- News events: like management change, regulatory penalty, major customer loss, competitor breakthrough
- Price and valuation: must clarify this is "valuation change" or "fundamental change", can't mix

If can't find evidence explaining change, must judge as **Unchanged** or **Can't judge**, can't use wording difference infer drift.

### A6: Output drift report

#### Report structure

```
One. Comparison object and time span
Two. Overall conclusion: thesis drift?
Three. Dimension drift table
Four. Evidence difference detail
Five. Valuation and number verification
Six. Action recommendation migration
Seven. Uncertainty and needed supplementary source
Eight. Next tracking focus
```

#### Dimension drift table

| Dimension | Old Judgment | New Judgment | Drift Direction | Trigger Evidence | Confidence |
|------|-------|-------|:--------:|---------|:------:|
| Valuation anchor | | | Improved / Unchanged / Weakened | | High/Mid/Low |
| Key assumption checklist | | | Improved / Unchanged / Weakened | | High/Mid/Low |
| Red-line checklist | | | Improved / Unchanged / Weakened | | High/Mid/Low |
| Management quality | | | Improved / Unchanged / Weakened | | High/Mid/Low |
| Competitive moat | | | Improved / Unchanged / Weakened | | High/Mid/Low |

**Unchanged line trigger evidence write `—`, don't fabricate evidence to fill table.**

#### Overall conclusion must answer

1. **Thesis drift?** Didn't drift / Positive drift / Negative drift / Insufficient evidence can't judge
2. **Drift from where?** Valuation / Fundamental / Management / Competitive / Red-line event
3. **Fact change or price change?** Clearly separate explanation
4. **How recommend action migrate?** Example: Watch → Buy, Buy → Hold, Hold → Reduce, Reduce → Exit
5. **What evidence next step need?** Next financial report / Regulatory disclosure / Management explanation / Competitor data

---

## Mode B: Automatic Snapshot Comparison

### B1: Find snapshots

In `reports/` find:
- `reports/{company-name}-thesis.md`
- `reports/{company-name}-thesis-*.md`
- `reports/{company-name}/` directory contains "thesis", "tesis", "tracking" report

Select earliest and most complete file as old report, newest as new report. If user specified date, use specified.

### B2: Prevent wrong pairing

Before comparison must confirm:
- Company name or stock code consistent
- Report dates different
- Both reports contain extractable thesis structure or research conclusion

If can't confirm same company, stop and request explicit path from user.

### B3: Execute Mode A

After finding two valid snapshots, execute Mode A completely.

---

## Mode C: Missing Baseline Processing

If found only one report or found no old snapshot:

1. Clearly state: **Can't execute thesis drift detection: missing comparable historical baseline**
2. Don't try to fabricate old thesis from memory or market impression
3. Guide user first use `/thesis-tracker {company-name} establish thesis` to establish structured baseline
4. If current report already sufficiently complete, can suggest save as `reports/{company-name}-thesis.md` as future drift detection baseline

Output format:

```
Can't execute thesis drift detection: missing historical baseline.

Already found:
- Current report: {path / not found}
- Historical baseline: not found

Suggestion:
1. First run /thesis-tracker {company-name} establish thesis
2. Next time new financial report or major event, then run /thesis-drift {company-name} old-report new-report
```

---

## Key Principles

- **Evidence priority over wording** — Synonymous rewrite not drift, only evidence change is drift
- **Fundamental priority over price** — Price fluctuation only affects valuation anchor, doesn't change business fundamental
- **Numbers must be verified** — All percentage, valuation multiple, target price difference must `tools/financial_rigor.py` verification
- **Uncertain then mark uncertain** — Missing source, inconsistent caliber, can't verify, can't make strong judgment
- **Red-line process separately** — Red-line trigger priority higher than cheap valuation, can't be covered by low PE
- **Output must be reproducible** — Each Improved / Weakened conclusion must traceable to specific evidence