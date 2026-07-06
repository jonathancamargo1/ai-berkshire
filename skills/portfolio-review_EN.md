# Portfolio Management: From "Research Company" to "Manage Portfolio"

Execute investment portfolio review and optimization for $ARGUMENTS.

**Supported input formats**:
- Portfolio holding, ex: `Tencent 30%, Meituan 20%, Maotai 20%, Nvidia 15%, Cash 15%`
- Or: `Tencent 500 shares @480 HKD, Meituan 1000 shares @130 HKD, ...`
- Or: `My portfolio` (if saved portfolio file `reports/portfolio-latest.md` exists)

&gt; "Diversification is protection against ignorance. If you know what you're doing, diversification is meaningless." —— Buffett
&gt;
&gt; "In all my years, truly good investment opportunities I could count on ten fingers." —— Li Lu

## Design Philosophy

Researching companies is only half of investing. The other half is **portfolio-level decisions**:
- How much to buy? (Position size)
- What money to use? (Capital source — new money or rebalance)
- Conflict with current holdings? (Correlation)
- What's the optimal portfolio? (Opportunity cost)

Buffett never looks at stocks in isolation — he's always thinking "is this the best thing I can do?".

## Execution Flow

### Step One: Parse Holdings

From input parse current holdings, standardize to format below:

| Target | Code | Quantity | Cost Price | Current Price | Market Value | Proportion | P/L |
|------|------|--------|-------|------|------|------|------|

If input only has proportions without amounts, analyze by proportions okay.

Simultaneously check if saved portfolio file exists (`reports/portfolio-latest.md`).

### Step Two: Get Latest Data

Use Task tool launch background Agent, via WebSearch parallel get each position:
1. Current stock price and valuation metrics (PE, PB, dividend yield)
2. Recent quarterly financial changes
3. Recent major events
4. Analyst consensus expectations

For each position use `tools/financial_rigor.py verify-valuation` validate data. Mark information richness (A/B/C).

### Step Three: Individual Position Health Check

Quick health check for each position:

| Target | Current PE | Buy Logic Changed? | Thesis Health | Recommendation |
|------|:------:|:--------------:|:---------:|----------|
| Tencent | 18x | No | 8/10 | Reasonable |
| Meituan | 25x | Yes | 6/10 | Slightly high |

Each position answer:
- [ ] If no position today, would still buy at current price?
- [ ] If can't trade tomorrow, comfortable holding 5 years?
- [ ] Is buy thesis still intact?

**Dyo Yupeng**: "If won't hold 10 years, shouldn't hold one day."

### Step Four: Portfolio-Level Analysis

#### 4.1 Concentration

| Metric | Current | Recommended Range |
|------|-------|----------|
| Largest position | | &lt;40% |
| Top 3 positions | | 50-80% |
| Total positions | | 5-15 |
| Cash proportion | | 10-30% |

**Li Lu**: 3-5 core positions, &gt;80% in top 3. But requires deep research.

#### 4.2 Correlation

| Position A | Position B | Type | Risk |
|-------|-------|---------|------|
| Tencent | Kuaishou | China Internet | Joint regulation |
| Nvidia | TSMC | AI supply chain | Synchronized capex |
| Meituan | Pinduoduo | China consumption | Macro synchronized |

#### 4.3 Opportunity Cost

Rank by expected annualized return:

| Rank | Target | Proportion | Expected Return | Certainty | Return×Certainty |
|:----:|------|:-------:|:----------:|:------:|:--------------:|
| 1 | | | | | |

**Key question**: Lowest-ranked position, expected return &gt; cash (4%)? If not, sell.

#### 4.4 Stress Test

| Scenario | Assumption | Impact |
|------|------|----------|
| Recession | Profit -20-30% | |
| China-US Conflict | 50% discount | |
| Rates Spike | 10-year → 6% | |
| Tech Bubble | PE -40% | |

### Step Five: Recommendations

#### 5.1 Rebalancing Actions

| Action | Target | Current | Recommended | Reason |
|------|------|:-------:|:-------:|----------|
| Increase | | | | |
| Reduce | | | | |
| Liquidate | | | | |
| Add New | | | | |
| Hold | | | | |

#### 5.2 Finding Alternatives

Use `/industry-research` or `/investment-checklist` — don't directly recommend stocks here.

#### 5.3 Cash Management

| Current | Recommended | Reason |
|:----------:|:----------:|----------|

**Buffett**: $382B cash today, &gt;25% of total.

### Step Six: Generate Report

#### Structure

```
One. Overview (Table + Pie Chart)
Two. Individual Position Health
Three. Portfolio Analysis
   - Concentration
   - Correlation
   - Opportunity Cost
   - Stress Test
Four. Rebalancing Recommendations
Five. Next Review Timing
```

#### Conclusion Must Clearly Answer

1. **Overall Health**: Excellent/Good/Needs Adjustment/Problematic
2. **Most Important Action**: Increase X/Reduce Y/Hold
3. **Biggest Risk**

### Step Seven: Save Portfolio File

Write to `reports/portfolio-latest.md`, include:
- Latest holdings table
- Review date and conclusion
- Rebalancing history (append)
- Next review reminder