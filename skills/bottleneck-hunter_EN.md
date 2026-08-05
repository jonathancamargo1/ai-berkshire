# Supply Chain Bottleneck Hunter: AI-Driven Bottleneck Scanning and Arbitrage Opportunity Discovery

Execute supply chain bottleneck scanning and arbitrage opportunity discovery for $ARGUMENTS.

## Core Philosophy

Don't ask "what stock does AI recommend", ask "if this trend keeps expanding, which link will run out of capacity first?"

Traditional investment research focuses on market leaders and known sectors. This system works backwards: **starting from the physical chokepoint of supply chains, finding the companies nobody notices but where the entire industry would have to stop if they ran out of stock**.

Excess returns come from: the first layer of bottlenecks (GPU, HBM, power) is already fully priced. The real alpha is in the **second and third layers** — optical modules, lasers, InP substrates, SOI wafers, epitaxy equipment, wafer-level testing, IC substrates, specialty fiberglass, etc.

## Step 1: Super-Trend Confirmation

### 1.1 Trend Selection Criteria

Don't fish for illusions in small winds, only pursue super-trends that meet ALL criteria:

| Criterion | Requirement | Verification Method |
|-----------|-------------|---------------------|
| Persistence | At least 3-5 years guaranteed growth | Search industry forecasts, capex plans |
| Physicality | Requires actual hardware/materials/equipment construction | Distinguish "software upgrade" from "physical expansion" |
| Scale | Global capex > $50 billion/year | Search capex guidance from major players |
| Acceleration | Demand growth > supply expansion speed | Compare demand growth rate vs capacity expansion plans |

### 1.2 Current Tracked Super-Trends List

Update with each run, initial list:

1. **AI Infrastructure Build-out** — data centers, GPU clusters, network interconnect, power
2. **Energy Transition** — nuclear restart, grid upgrade, energy storage
3. **Defense Modernization** — Western military spending upswing, supply chain reconstruction
4. **Semiconductor Re-industrialization** — US/EU/Japan subsidies for fab construction, equipment/material bottlenecks
5. **Space Economy** — satellite internet, launch frequency acceleration

If user specifies a specific trend (like "AI Infrastructure"), focus only on that trend.

### 1.3 Trend Verification Output

```
Trend Name:
Core Driver: (one sentence)
Verification Events That Have Occurred (at least 3):
  1. [Date] [Event] [Source]
  2.
  3.
Capital Expenditure Scale: Approximately $XX billion/year, growth YY%
Supply-Demand Gap Assessment: Demand growth > supply expansion speed? Yes/No/Uncertain
Trend Confirmation: ✅ Trackable / ❌ Insufficient evidence, not tracking yet
```

## Step 2: Supply Chain Physical Decomposition

### 2.1 Layered Decomposition Framework

**Don't stay at concept level, decompose to physical entities**.

```
Layer 0 (End): Final product/service
    |
Layer 1 (Core Components): Already heavily market-observed core hardware
    |                 ⬆ Pricing adequate, alpha limited
    |─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
    |                 ⬇ Low attention, alpha concentrated
    |
Layer 2 (Sub-components/Materials): Parts and materials supporting core components
    |
Layer 3 (Equipment/Raw Materials): Equipment and raw materials for making sub-components
    |
Layer 4 (Infrastructure): Power, cooling, land, talent, certification
```

### 2.2 Decomposition Template: AI Infrastructure Example

```
Layer 0: AI model training/inference service
Layer 1: GPU/accelerator, HBM memory, server, data center
Layer 2 (Priority Scanning Area):
  ├─ Network Interconnect: optical module, fiber, switch chip, copper cable
  ├─ Optical Communication Core: laser (EML/VCSEL/CW), modulator, photo detector
  ├─ Semiconductor Material: InP substrate, GaAs substrate, SOI wafer, SiC substrate
  ├─ Advanced Packaging: CoWoS substrate, HBM TSV, ABF base film
  ├─ PCB/Substrate: high-frequency high-speed PCB, IC substrate, specialty fiberglass
  ├─ Testing: wafer-level testing (Probe Card), aging test, ATE
  ├─ Cooling/Heat Dissipation: liquid cooling system, CDU, immersion cooling fluid
  └─ Power Connectivity: busway, UPS, distribution panel, transformer
Layer 3:
  ├─ Epitaxy Equipment: MOCVD, MBE
  ├─ Lithography/Etch: specialty wavelength lithography, InP etch
  ├─ Raw Materials: high-purity metals (indium, gallium, germanium), special gas, target
  └─ Certification/Standards: MSA standard, Telcordia certification
Layer 4:
  ├─ Power: nuclear, natural gas generation, transmission and distribution
  ├─ Cooling water/heat dissipation infrastructure
  └─ Data center land/licenses
```

### 2.3 Decomposition of Other Trends

For each confirmed super-trend, execute similar decomposition. Use WebSearch:
- "{trend} supply chain bottleneck 2026"
- "{trend} shortage critical component"
- "{trend} capacity constraint"
- "{trend} sole source supplier"

## Step 3: Bottleneck Identification — Finding the "Throat"

### 3.1 6 Bottleneck Determination Criteria

For each segment in Layers 2-3, systematically evaluate:

| # | Criterion | Question | Score |
|---|-----------|----------|-------|
| 1 | **Supply Concentration** | Global suppliers ≤ 3? | 🔴 ≤2 / 🟡 3-5 / 🟢 >5 |
| 2 | **Production Expansion Cycle** | How long for new capacity? | 🔴 >2 years / 🟡 1-2 years / 🟢 <1 year |
| 3 | **Substitution Difficulty** | Can be replaced by other tech/material? | 🔴 Non-substitutable / 🟡 Partially / 🟢 Easy |
| 4 | **Capacity Utilization Rate** | Current capacity utilization? | 🔴 >90% / 🟡 70-90% / 🟢 <70% |
| 5 | **Demand Growth** | Downstream demand growth rate? | 🔴 >50%/year / 🟡 20-50% / 🟢 <20% |
| 6 | **Customer Validation Cycle** | Time needed for new supplier validation? | 🔴 >1 year / 🟡 6-12 months / 🟢 <6 months |

**Bottleneck Rating**:
- 🔴🔴🔴 ≥4 red → **S-grade Bottleneck** (single point of failure, highest priority)
- 🔴🔴 3 red → **A-grade Bottleneck** (severely constrained)
- 🔴 1-2 red → **B-grade Bottleneck** (under pressure but manageable)
- No red → Not a bottleneck, skip

### 3.2 Bottleneck Map Output

```
Supply Chain Bottleneck Map — {Trend Name}
Update Date: YYYY-MM-DD

S-grade Bottlenecks (Single Point of Failure):
  1. [Segment Name] — [Reason in one sentence] — Suppliers: [Company List]
  2.

A-grade Bottlenecks (Severely Constrained):
  1.
  2.

B-grade Bottlenecks (Under Pressure):
  1.
  2.

Recent Changes (vs. previous scan):
  - [New/Upgraded/Downgraded/Resolved] [Segment Name] — [Reason]
```

## Step 4: Company Selection — From Bottleneck to Security

### 4.1 For Each S-grade and A-grade Bottleneck, Find All Related Listed Companies

Search Methods:
- WebSearch "{bottleneck segment name} supplier listed company"
- WebSearch "{bottleneck product name} manufacturer stock"
- WebSearch "{bottleneck product market share} company"

### 4.2 Pre-filter Criteria (Quick Elimination)

| Criterion | Requirement | Rationale |
|-----------|-------------|----------|
| Listing Status | Listed (A/HK/US/JP/TW/EU) | Tradeable |
| Bottleneck Business % | >30% revenue from bottleneck segment | Purity |
| Market Cap | Preferably < $100 billion USD | Large cap already fully priced |
| Liquidity | Average daily volume > $1 million USD | Can enter/exit |

### 4.2.1 Valuation Check (Mandatory, Cannot Be Skipped)

**Real bottleneck ≠ Investment opportunity.** You MUST calculate PS and PE for each company and annotate in report. Use the following composite criteria to determine if valuation is compromised:

#### Valuation Red Light (Meeting any → Signal strength capped at ★★, tag "⚠️ Valuation Compromised")

1. **Market Cap > 20% of TAM**: Company market cap already exceeds 20% of total addressable market, indicating growth expectations are over-internalized
2. **PS > 30x AND Revenue Growth < 100%**: High valuation but growth insufficient to support. Companies with growth >100% exempt from PS red line, but still tag "⚠️ High valuation requires continuous growth validation"
3. **Market Cap > 10x Optimistic 5-Year Revenue Forecast**: Even if all optimistic assumptions realized, current pricing still too high
4. **Stock Price Doubled Within 60 Days Post-Secondary Offering**: Strong emotion-driven signal, downgrade signal strength one level

#### Valuation Yellow Light (Requires Additional Explanation, Otherwise Downgrade)

1. **Loss-Making + PS > 15x**: Allow entry to ★★★ but MUST explain path to profitability and timeline
2. **PS 5x Higher Than Profitable Peers in Same Sector**: MUST explain premium source (market share, growth differential, moat differential)
3. **PE > 80x**: Calculate PEG and explain if growth speed supports

#### Valuation Green Light (Bonus Items)

- PS < 10x AND revenue growing → Signal strength can upgrade one level
- PE < 30x AND with moat → Tag "valuation has safety margin"

#### Valuation Reasonableness Check (Mandatory)

For each security answer: "At current market cap, assuming most optimistic scenario fully realized, exiting at 25x PE in 10 years, what's the annualized return?" Annualized return < 10% → tag "Current price lacks safety margin".

**Note**: Valuation check purpose is to avoid recommending "PS 100x loss-making company", not to eliminate all high-valuation companies. Key is whether growth speed, TAM, and competitive structure can support current valuation, requiring specific analysis rather than mechanical rules.

### 4.3 Deep Screening Dimensions

For companies passing pre-filter, evaluate each:

```
## {Company Name} ({Code})

**Bottleneck Positioning**:
- Specific location in supply chain
- Market share: Global #X, XX% share
- Known customer list

**Capacity and Expansion**:
- Current capacity / Utilization rate
- Expansion plan / Timeline
- Capital needed for expansion vs. existing cash

**Financial Snapshot**:
- Market cap / Revenue / Profit / Growth rate
- Bottleneck business revenue proportion
- Gross margin trend (tighter bottleneck = margin should rise)

**Risk Checklist**:
- [ ] Substitution tech risk: Can be bypassed?
- [ ] Dilution risk: Lots of issuance/convertibles?
- [ ] Geography risk: Sensitive region/export controlled?
- [ ] Management risk: Bad track record?
- [ ] Customer concentration risk: Over-dependent on single customer?
- [ ] Valuation compromised: Does current valuation already reflect 3 years growth?

**Bottleneck Persistence Assessment**:
- When will this bottleneck be eliminated?
- What does the company have after elimination?
- One-time or recurring?
```

## Step 5: Cross-Verification — Don't Listen to Just One Story

### 5.1 Positive Direction Verification

| Verification Item | Question | Search Method |
|------------------|----------|----------------|
| Customer Validation | Have major customers signed/ramped? | Search company announcements, customer financial report mentions |
| Revenue Validation | Has bottleneck appeared in revenue growth? | Search latest 2-3 quarterly earnings |
| Price Validation | Is product pricing up? | Search industry pricing, analyst reports |
| Capacity Validation | Is capacity actually tight? | Search lead time data, customer complaints |
| Capital Validation | Is there expansion capex? | Search company capex guidance |

### 5.2 Negative Direction Verification (Munger-style)

| Negative Question | Significance |
|------------------|-------------|
| Why don't smart people buy this stock? | Find known bearish arguments |
| Can this bottleneck be circumvented? What's the alternative route? | Technical route risks |
| Can China/other players quickly replicate capacity? | Supply shock risk |
| If end-user demand falls 50%, what happens to this company? | Downside sensitivity |
| Has management done large secondary offerings at peaks? | Management trustworthiness |
| What growth assumptions does current valuation imply? | Valuation reasonableness |

### 5.3 Signal Cross-Verification

- Are all companies in same bottleneck rising? (Sector validation)
- Do downstream customers mention supply tightness in reports? (Customer validation)
- Do industry associations/research have relevant data? (Third-party validation)

## Step 6: Output — Bottleneck Opportunity Dashboard

### 6.1 Bottleneck Opportunity Ranking Table

| Rank | Company | Code | Market Cap | Annual Revenue | PS | PE | Bottleneck Segment | Bottleneck Grade | Market Share | Revenue Growth | Signal Strength | Valuation Judgment |
|------|---------|------|------------|----------------|----|----|--------------------|-------------------|---------------|-----------------|-----------------|---------------------|
| 1 | | | | | x | x | | S/A | | | ★1-5 | Reasonable/Premium/Excessive |

**Mandatory Fields**: Market cap, annual revenue, PS, PE cannot use "pending verification". If unable to obtain financial data, signal strength cannot exceed ★★.

Signal Strength Rating (valuation check result directly affects rating):
- ★★★★★ Multiple cross-verifications, customer in ramp-up, revenue reflected, valuation green light (reasonable PS + profitable or near-profitable)
- ★★★★ Most verifications passed, valuation green or yellow light (requires explanation)
- ★★★ Logic sound but some pending verification, yellow light acceptable (e.g. high-growth early-stage company)
- ★★ Early signal, or bottleneck logic sound but valuation red light (market cap >20% TAM, PS>30x without sufficient growth, market cap well exceeds 5-year forecast)
- ★ Pure concept, unverified

### 6.2 One-Page Summary For Each Opportunity

```
🎯 {Company Name} ({Code}) — {Bottleneck Positioning in One Sentence}

Why It's a Bottleneck:
(2-3 sentences explaining why this segment is the chokepoint)

Why This Company:
(2-3 sentences explaining why this company over others)

Catalyst Timeline:
- Near-term (1-3 months): [Specific event, e.g. earnings, capacity investment, customer validation]
- Medium-term (3-12 months): [Industry trend, expansion milestone]

Key Risks:
1.
2.

Key Data: Market Cap $XX / Annual Revenue $XX / PS Xx / PE Xx / Revenue Growth XX% / Bottleneck Business % XX%

Valuation Safety Margin Verification: At current market cap, exiting at 25x PE in 10 years, requires net profit reach $XX, corresponding annual revenue $XX (X times today), annualized return XX%. Conclusion: Has/No safety margin.

Cross-Verification Status: ✅ Customer Verified / ✅ Revenue Verified / ✅ Reasonable Valuation / ⚠️ Valuation Excessive / ❌ Unverified Item

Conclusion: Worth deeper research / Add to watchlist / Not tracking for now
```

### 6.3 Action Recommendation

| Security | Recommended Action | Rationale |
|----------|------------------|----------|
| A | Execute `/investment-team` deep research | S-grade bottleneck + multiple verifications |
| B | Add to watchlist, wait next quarterly report | Logic sound but revenue not yet reflected |
| C | Not tracking for now | Alternative technology risk too high |

## Step 7: Bottleneck Map Maintenance — Dynamic Update

### 7.1 Incremental Update With Each Run

1. Check if identified bottlenecks still valid
   - Any new suppliers entering?
   - Has capacity expanded to resolve bottleneck?
   - Any breakthrough in alternative technology?

2. Scan for newly emerging bottlenecks
   - Search last 7 days supply chain / shortage / bottleneck news
   - Check supply chain disclosures in earnings season

3. Update bottleneck ratings (upgrade/downgrade/resolved)

### 7.2 State File

Maintain in `reports/bottleneck-map/` directory:
- `master-map.md` — Overall bottleneck map (continuous update)
- `watchlist.md` — Watchlist (continuous update)
- `YYYY-MM-DD/` — One folder per day, containing all scan reports for that day
- `deep-dive/` — Companies under deep analysis in individual files

## Hourly Scanning Mode (Scheduled Task Use)

Execute once per hour, using "output report only when there's substance" mode:

### Scan Flow (Each Hour)

1. **News Scan**: Search supply chain news from past 1-2 hours
   - Keywords: supply chain bottleneck, shortage, capacity constraint, allocation, lead time, sole source, 瓶颈, 缺货, 产能, 涨价
   - Coverage: English + Chinese sources
2. **Market Signal**: Check price changes of tracked companies (focus on anomalies >5%)
3. **Earnings/Announcements**: Check if bottleneck-relevant companies released earnings or important announcements
4. **Valuation Opportunity**: Check if watchlist companies entered buy zone from overall market decline
5. **Decide If Output Report**:
   - New bottleneck signal, clear security opportunity, significant state change → **Output Report**
   - No new discoveries → **No report**, just log "This round no new signals"

### Report Output Rules

**One folder per day**: `reports/bottleneck-map/YYYY-MM-DD/`

**File Naming Convention** (see filename quickly if has securities):

| Situation | File Name Format | Example |
|-----------|-----------------|----------|
| Found clear security | `HH-MM-code1-code2.md` | `09-00-FORM-IBDN.md` |
| Has bottleneck signal but no clear security | `HH-MM-signal-scan.md` | `14-00-signal-scan.md` |
| No new discoveries | No file generated | — |

**Security code in filename = Passed valuation check, worth deeper research.** Companies appearing only in signal scan phase but failing valuation do NOT go in filename.

### Report Template (When Has Security)

```markdown
# Bottleneck Hunter — YYYY-MM-DD HH:MM

## Clear Security

### {Company Name} ({Code}) — {Bottleneck Positioning in One Sentence}

**Why Worth Attention Now**: (Specific event or data change that triggered this scan)

**Bottleneck Positioning**: Layer X, {Segment Name}, Bottleneck Grade S/A/B
**Financial Snapshot**: Market Cap $XX / Annual Revenue $XX / PS Xx / PE Xx / Revenue Growth XX%
**Valuation Check**: Red/Yellow/Green Light (Specific explanation)
**Valuation Safety Margin Verification**: Using 25x PE exit in 10 years method, annualized return XX%

**Bullish Logic** (2-3 points):
1.
2.

**Bearish Logic** (2-3 points):
1.
2.

**Recommendation**: Execute deep research / Add to watchlist / Wait for better price

---

## Other Signals (No Clear Security)

| Segment | Signal | Source | Initial Judgment |
|---------|--------|--------|-------------------|

## Watchlist Status Changes

(Upgrade/Downgrade/New/Removed, no changes write "No changes")
```

### Report Template (Signal Scan Only)

```markdown
# Bottleneck Hunter Signal Scan — YYYY-MM-DD HH:MM

## New Signals

| Segment | Signal Description | Source | Has Tradeable Security? | Next Step |
|---------|------|------|--------|--|

## Watchlist Status

No changes / Has changes (list)
```

## AI Research Bias Awareness

| Bias | Manifestation | Counter-measure |
|------|-------|----------|
| Large-cap Preference | Search results dominated by large-cap companies | Deliberately search small-cap suppliers, add "small cap" keyword |
| English Preference | Miss Japanese, Korean, Taiwan companies | Search Japan/Korea/Taiwan market suppliers |
| Narrative Preference | Attracted by "AI concept" label | Focus only on actual supply chain position, ignore market label |
| Confirmation Bias | Seek confirmation after finding bottleneck | Force negative direction verification (Step 5) |
| Recency Bias | Depends on outdated information | Prioritize last 30 days data |

## Core Principles (Maximum Priority)

1. **Don't let AI recommend stocks, let AI decompose supply chains** — Question matters more than answer
2. **Physics first** — Only focus on segments requiring actual physical products/materials/equipment
3. **Second and third layers** — Don't pursue first-layer bottlenecks already fully priced
4. **Cross-verification** — Every conclusion needs at least 2 independent sources
5. **Honest about uncertainty** — If can't find data, write "insufficient data", don't fill with assumptions
6. **Bottlenecks have shelf life** — Every bottleneck eventually gets resolved, key is timing the window
7. **Small cap ≠ good opportunity** — Small cap can also be bad company, must pass financial quality gate
8. **Real bottleneck ≠ investment opportunity** — A company can sit on the tightest bottleneck, but if PS>30x or still loss-making, current price isn't a buy point. **Valuation is hard gate, cannot be overridden by bottleneck purity, signal strength, or narrative attractiveness.** Better to miss a bottleneck stock that rose than to buy a loss-making company at PS 100x.
9. **Follow CLAUDE.md objectivity principle** — No pre-set bias, data first then conclusion

## Output Requirements

1. **Report Location**:
   - Complete Scan: `reports/bottleneck-map/{trend-name}-bottleneck-{YYYYMMDD}.md`
   - Daily Scan: `reports/bottleneck-map/daily/{YYYY-MM-DD}-{am/pm}.md`
   - Overall Bottleneck Map: `reports/bottleneck-map/master-map.md`
   - Watchlist: `reports/bottleneck-map/watchlist.md`
2. **Language**: Chinese
3. **Style**: Direct, sharp, no fluff
4. **Data**: All data tagged with source; estimated values tagged "estimated"
5. **No Pre-set Stance**: Data first → Logic → Conclusion
6. **Both Sides**: Every core judgment has counter-argument