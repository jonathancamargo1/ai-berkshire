# Investment Team Skill - Four Masters Parallel Analysis Framework

Conduct team-based investment research analysis for $ARGUMENTS. Use Team tool to create a true multi-agent research team running in parallel.

## Execution Flow

### Step One: Display Team Structure

Display the following team structure, confirm with user before launching:

| Role | Responsibility | Analysis Framework |
|------|------------------|------------------|
| **team-lead**(yourself) | Overall coordination, research synthesis, final report | Four masters integrated framework |
| **business-analyst** | Business model & moat analysis | Duan Yongping perspective |
| **financial-analyst** | Financial statements & valuation analysis | Warren Buffett perspective |
| **industry-researcher** | Industry landscape & competitive position | Charlie Munger perspective |
| **risk-assessor** | Risk evaluation & management quality | Li Lu perspective |

### Step One-and-a-Half: AI Research Bias Assessment

Before creating team, display to user the company's "AI-researchability" assessment:

**Information Richness Rating** (determines research strategy):
| Level | Characteristics | Research Strategy Adjustment |
|-------|-----------------|----------------------------|
| Level A (Information Abundant) | Listed for years, broad analyst coverage | Team focus on **reverse verification** and **non-consensus perspectives**, avoid outputting consensus-aligned "correct but useless talk" |
| Level B (Information Adequate) | Recently listed, limited coverage | Each Agent's inferred data must be marked with confidence level, team-lead synthesis must mark "data sufficiency" |
| Level C (Information Scarce) | Niche/Recently listed/Emerging market | Team converts to "first-principles mode": don't pursue report completeness, focus on few core questions about business essence |

**Key Reminder**: more information ≠ higher certainty, less information ≠ lower certainty. Confidence AI can generate ≠ real investment certainty. Certainty comes from business model itself, not amount of materials.

Communicate rating to each Agent, affecting their research approach.

### Step Two: Create Team

Use TeamCreate to create team:
- team_name: `{company_name}-research` (lowercase English, e.g., `meituan-research`)
- agent_type: `team-lead`

### Step Three: Create 4 Tasks

Use TaskCreate to create following 4 tasks (each with subject, description, activeForm):

#### Task 1: Business Model Analysis
- subject: `Analyze {company_name} business model, moat and user value`
- description includes:
  1. Business model essence: core business definition, revenue structure breakdown
  2. How platform/product flywheel effect operates
  3. Moat analysis: brand/switching costs/network effects/scale effects/technology barriers, validate each
  4. User/customer value: what unique value created for each party
  5. Business matrix and synergistic effects
  6. Duan Yongping "good business" standard assessment: differentiation, pricing power, sustainable competitive advantage
  7. Require searching latest public information: financial statements, industry reports

#### Task 2: Financial and Valuation Analysis
- subject: `Analyze {company_name} financial data, profitability and valuation`
- description includes:
  1. 3-5 year trend of revenue, net profit, operating profit
  2. Profitability indicators: ROE, ROA, gross margin, operating margin
  3. Cash flow analysis: operating cash flow, free cash flow, capex
  4. Balance sheet health: cash reserves, debt ratio, liquidity
  5. Valuation analysis: PE/PS/PB/EV, comparison with history and peers
  6. Safety margin assessment: intrinsic value vs current stock price
  7. **Financial Rigor Validation (MUST use Bash to call tools, no mental calculation)**:
     - Market cap verification: `python3 tools/financial_rigor.py verify-market-cap --price {price} --shares {shares} --reported {reported_market_cap} --currency {currency}`
     - Valuation verification: `python3 tools/financial_rigor.py verify-valuation --price {price} --eps {EPS} --bvps {book_value_per_share}`
     - Key data cross-validation: `python3 tools/financial_rigor.py cross-validate --field {field} --values '{JSON}' --unit {unit}`
     - Three-scenario valuation: `python3 tools/financial_rigor.py three-scenario --price {price} --eps {EPS} --shares {shares_billions} --growth {bullish} {base} {bearish} --pe {bullish_PE} {base_PE} {bearish_PE}`
     - Embed tool output results directly in report as validation records

#### Task 3: Industry and Competitive Analysis
- subject: `Analyze {industry} industry landscape and {company_name} competitive position`
- description includes:
  1. Industry scale and growth: market size, growth rate, penetration rate
  2. Competitive landscape: main competitors' market share, competitive strategy comparison
  3. Core competitor threat assessment: analyze each major competitor
  4. Landscape of each segment
  5. Industry trends: technology changes, policy impact, new entrants
  6. Value chain analysis: value distribution across upstream, midstream, downstream
  7. Require searching latest industry data and competitive dynamics

#### Task 4: Risk and Management Assessment
- subject: `Assess {company_name} investment risk and management quality`
- description includes:
  1. Management assessment: CEO circle of competence, integrity, strategic vision, capital allocation ability, historical decision quality
  2. Regulatory risk: current and potential regulatory impact
  3. Competitive risk: threat level of each competitor
  4. Business risk: new business losses, expansion uncertainty
  5. Macroeconomic risk: economic cycle and industry cycle impact
  6. Governance structure: equity structure, related transactions, shareholder return policy
  7. Long-term certainty: how will company be in 10 years? What could disrupt its business model?
  8. Require searching latest regulatory dynamics, management commentary

### Step Four: Launch 4 Parallel Agents

Use Task tool to simultaneously launch 4 Agents (**MUST call Task 4 times in same message in parallel**):

Each Agent configured as:
- `subagent_type`: `general-purpose`
- `run_in_background`: `true`
- `team_name`: corresponding team name
- `name`: corresponding role name (business-analyst / financial-analyst / industry-researcher / risk-assessor)

Each Agent prompt template:

You are "{role_name}" of the {company_name} investment research team, responsible for analyzing {company_name} from {master_name}'s investment perspective.

Complete Task #{task_number}: {task_subject}

Specific requirements:
{task_description_content}

**Research Method**:
- Use WebSearch to search latest public information (financial statements, industry reports, news)
- **Financial data MUST come from two independent sources**, execute per `skills/financial-data.md` standards (US: macrotrends+stockanalysis; HK: aastocks+macrotrends; China: Eastmoney+巨潮资讯), error between sources >1% must be marked
- Ensure data accuracy, mark key data with source
- Thorough analysis, not superficial

**Output Requirements**:
- Report detailed, use Markdown tables to present key data
- Each analysis dimension must have clear conclusion and rating
- Report end must have overall conclusion of this dimension

**After Completion**:
1. Use TaskUpdate to mark task #
{task_number} as completed
2. Use SendMessage to send complete analysis report to team-lead (type: "message", recipient: "team-lead")

### Step Five: Receive Reports and Track Progress

- Display real-time progress table (which Agents completed, which still researching)
- Each report received, update progress and display report's key points (3-5 items)
- Wait until all 4 reports are ready

### Step Six: Close Team Members

All reports received, send shutdown_request to 4 Agents (use SendMessage, type: "shutdown_request").

### Step Seven: Synthesize Final Report

Synthesize 4 analysis reports, output final report with following structure:

---

#### 1. One-Sentence Conclusion
> Use one paragraph (50-100 words) to summarize whether worth investing and core logic

#### 2. Four-Dimension Rating Table
| Dimension | Framework | Rating(1-5 stars) | Core Judgment |
|-----------|-----------|-----------------|---------------|

Integrated Rating: X / 5

#### 3. Key Data Overview
Table of key financial and operational indicators (last 2 years comparison)

#### 4. Summary of Each Dimension Analysis
Each dimension extract 3-5 most important findings

#### 5. Investment Thesis (Bull vs Bear)
- 🟢 Bullish logic (5-7 items)
- 🔴 Bearish logic (5-7 items)

#### 6. Buffett Pre-Purchase Checklist
| # | Checklist Item | Passed? | Explanation |
|---|----------------|--------|-------------|
10 core checklist items, evaluate each

#### 7. Final Investment Recommendation
- Qualitative judgment table (business quality/management/valuation/timing)
- Layered operational recommendation table (aggressive/prudent/conservative → recommendation + price range)
- Key catalysts (add signal/reduce signal each 3-5 items)

#### 8. Summary Paragraph
100-200 words final summary

---

### Step Eight: Save Report

Write complete final report to `~/{company_name}_investment_research_report_{date}.md` (date format YYYYMMDD).

### Step Nine: Data Sampling Audit (Approval Flow)

```bash
# Step 1 — Extract audit checklist (15% random sampling)
python3 tools/report_audit.py extract \
  --report <report_file_path>

# Step 2 — For each checklist item, get data from reliable source (see skills/financial-data.md)

# Step 3 — Output approval/rejection verdict
python3 tools/report_audit.py verdict \
  --results '<filled_JSON>' \
  --report <report_file_name>
```

**【APPROVED】** All passed → Report ready to publish; **【REJECTED】** Some failed → Correct and re-audit.

### Step Ten: Clean Up Team

Use TeamDelete to clean up team resources.

## Important Notes

1. **4 Agents MUST be launched in parallel** — call Task 4 times in same message
2. **Agents report via SendMessage** — not file collaboration, but message communication
3. **Data accuracy** — require Agents to use WebSearch for latest data, cross-validate key data
4. **Conclusion must be clear** — don't avoid giving buy/watch/avoid recommendation and specific price range
5. **All analysis must be data-supported** — attach data sources
6. **Patience needed** — 4 Agent research takes several minutes, update user progress in real-time
7. **Anti-bias awareness** — team-lead when synthesizing MUST assess: is each Agent's analysis limited by data sufficiency? Do all converge too much with market consensus? Final report must include "information sufficiency rating" and "AI research limitation statement"
8. **Honesty principle when information scarce** — prefer leaving blank in report marked "insufficient data" rather than using assumption to fill structure and fake certainty