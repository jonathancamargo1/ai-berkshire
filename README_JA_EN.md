Portuguese | [English](README_EN.md) | [中文](README.md)

> The English version is maintained by the community. If the content is not up to date, please refer to the Chinese or Portuguese version as the source of truth.

[![GitHub Trending](https://trendshift.io/api/badge/repositories/63696)](https://trendshift.io/repositories/63696)

# AI Berkshire — Value Investment Research Framework for the AI Era

> "Price is what you pay, value is what you get." — Warren Buffett
>
> Redefine research depth and efficiency with AI.

**AI Berkshire** is a collection of investment research Skills compatible with Claude Code and Codex. We systematize the methodologies of four value investing giants — Buffett, Munger, Duan Yongping, and Li Lu — and deliver professional-grade research through AI agents.

1 person + Claude Code / Codex = An entire investment research team.

[Performance](#performance) · [Why Not Ask AI Directly?](#why-not-ask-ai-directly) · [Skills List](#skills-list19-skills) · [Quick Start](#quick-start) · [Reports](#real-research-reports) · [Design Philosophy](#design-philosophy)

---

## Performance

> This is not a paper simulation. This framework is backed by an audited portfolio with real capital.

### 2024 Full Year Return: +69.29%

<img src="assets/2024-returns.jpg" width="300" />

### 2025 Full Year Return: +66.38%

<img src="assets/2025-returns.jpg" width="300" />

### Benchmark Comparison

| Benchmark | Full Year 2024 | Full Year 2025 |
|-----------|---|---|
| **This Framework (Actual)** | **+69.29%** | **+66.38%** |
| Hang Seng Index | +17.67% | +27.77% |
| S&P 500 | +23.31% | +16.39% |
| CSI 300 | +14.68% | +17.66% |
| NASDAQ Composite | +28.64% | +20.36% |

**2024 Alpha**: Outperformed S&P 500 by **46 percentage points** and Hang Seng by **52 percentage points**

**2025 Alpha**: Outperformed S&P 500 by **50 percentage points** and Hang Seng by **39 percentage points**

**2-year cumulative actual return exceeds 14.6 million yuan**, with consistent outperformance of major global indices for 2 consecutive years.

> *Disclaimer: Past performance does not guarantee future results. Screenshots are from a real brokerage account (Futu Securities).*

---

## Why Not Ask AI Directly?

You can ask Claude: "Is PDD (Pinduoduo) a buy?" You'll get a balanced analysis with "on one hand... on the other hand..." and it will end with "investments involve risk, consider carefully."

**That analysis looks correct, but it's unusable for real decisions.**

AI Berkshire doesn't solve the problem "can AI analyze?", but rather **the quality of analysis and discipline in decision-making**. Here's what's different.

### 1. Force Decision — No Ambiguity

If you ask AI directly, you get analysis that's "convenient for both sides". AI Berkshire forces specific outputs: **Pass / Fail / Gray Zone**, with concrete price ranges and layered recommendations.

> Response to a naive question to AI: *"PDD has growth potential, but there's competitive pressure. Investors..."*
>
> AI Berkshire output:

> | Strategy | Recommendation | Price Range |
> |----------|---|---|
> | Aggressive | Build 20% position at current price | $95–105 |
> | Moderate | Wait for buyback policy clarification | $85–95 |
> | Conservative | Fails 10-year certainty criteria — Pass | — |
>
> **Mirror Test**: If you can't explain in 5 sentences = Don't buy. No exceptions.

### 2. Dialectic Between 4 Giants — Not a Single Perspective

Not "analyze this using Buffett's method". The 4 viewpoints create **real tensions and contradictions** —

Using PDD as an example:
- **Duan Yongping** (Business Model): Excellent business, C2M model hard to replicate → 3.7/5
- **Buffett** (Financial/Valuation): P/E ex-cash just 6.3x, cash machine → 4.4/5
- **Munger** (Reverse Thinking): Moat shallower than it appears — Douyin reached 4 trillion yuan GMV in 3 years → 3.5/5
- **Li Lu** (Long-term Certainty): Management culture concern, uncertain in 10 years → 2.0/5

**Buffett says "really cheap" while Li Lu says "if uncertain, don't buy"** — This collision is the reality of investment decision-making. A single prompt doesn't generate this multi-perspective dialectic, which is why it prevents blind spots.

### 3. Structured Bias Neutralization Mechanism

AI's greatest danger is not giving wrong answers, but **giving answers that seem right but don't survive scrutiny**. AI Berkshire embeds multiple "deception-prevention" layers in the process:

| Mechanism | Problem It Solves | Example |
|---|---|---|
| **Information Richness Assessment (A/B/C)** | Prevents illusion "more data = more certainty" | Pop Mart is B-rated: limited data, estimates flagged with confidence |
| **Munger Reverse Test** | Forces consideration of failure scenarios | "How could PDD collapse?" → List 5 scenarios with probabilities |
| **Instant Death Checklist** | 8 red lines, any one disqualifies | Management integrity issue → Instant rejection regardless of valuation |
| **Contrary Check** | Avoid thinking like the crowd | "Why are smart people shorting this?" → Surface overlooked risks |
| **Intellectual Honesty** | Prioritize "I don't know" | Data gaps marked as "Gray Zone", not filled with speculation |

### 4. Financial Data Precision

LLMs are unreliable at arithmetic. Getting P/E off by a digit or confusing HKD with CNY can lead to catastrophic investment decisions.

**Real Case**: In Tencent analysis, different sources reported market cap in "billions of HKD" vs "billions of CNY". AI Berkshire approach:

```bash
# Manual verification of market cap: Price × Outstanding Shares, compared with reported data
python3 tools/financial_rigor.py verify-market-cap \
  --price 510 --shares 9.11e9 --reported 4.65e12 --currency HKD
# ✅ Verified — Deviation only 0.08%
```

All calculations use Python `decimal.Decimal` (precise decimal arithmetic), never `float`. Critical data requires cross-validation from at least 2 independent sources.

### 5. Reproducible Research Process

If you ask AI directly, format, depth, and coverage vary each time — today's Tencent analysis might have a moat score, but tomorrow's Meituan analysis might forget it.

AI Berkshire guarantees: **Same input → Output consistent in structure, uniform in depth**. This enables:
- Comparing 7 companies side-by-side with identical scoring criteria
- Re-analyzing the same company 6 months later and directly comparing changes
- Aligning research outputs across team members

> Real output — Screening 7 companies with identical checklist:
>
> | Company | Decision | Circle of Competence | Excellent Business | Moat | Management | Safety Margin | Overall |
> |---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
> | Kweichow Moutai | ✅ Pass | ★★★★★ | ★★★★★ | ★★★★★ | ★★★☆☆ | ★★★★☆ | 4.7 |
> | Tencent | ✅ Pass | ★★★★☆ | ★★★★★ | ★★★★★ | ★★★★★ | ★★★★☆ | 4.7 |
> | NVIDIA | ✅ Conditional | ★★★★☆ | ★★★★★ | ★★★★★ | ★★★★★ | ★★★☆☆ | 4.3 |
> | Meituan | ✅ Conditional | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | 4.0 |
> | Kuaishou | ✅ Conditional | ★★★☆☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★★ | 4.0 |
> | Pinduoduo | ❓ Gray | ★★★★☆ | ★★★★☆ | ★★★☆☆ | ★★★☆☆ | ★★★★★ | 3.8 |
> | Pop Mart | ❓ Gray | ★★★☆☆ | ★★★★☆ | ★★★★☆ | ★★★★★ | ★★★☆☆ | 3.7 |

### 6. Multi-Agent Parallel Processing = Multiplication of Research Depth

`/investment-team` launches 4 independent agents **simultaneously** to research one company. Each agent conducts its own web searches, cross-validates data, and reaches independent conclusions. It's not one prompt split into 4 sections — it's 4 "analysts" each conducting complete research, with a team lead consolidating the final judgment.

If you ask AI directly, there's only one context window. 4 parallel agents mean 4x the search volume, 4x the information sources, 4 independent perspectives.

<p align="center">
  <img src="assets/team-core-en.svg" alt="Team Lead Running 4 Agents in Parallel" width="720" />
</p>

### In One Sentence

> **A regular user asking AI gets "an analysis that seems right". With AI Berkshire, you get "a research report actually usable for decision-making".**

---

## Architecture

<p align="center">
  <img src="assets/architecture-en.svg" alt="AI Berkshire Architecture" width="760" />
</p>

**3-Layer Design Philosophy**:
- **Skills Layer**: Abstract "what you want to do" into 19 clear entry points — deep research, earnings analysis, industry screening, portfolio management, thinking tools. Choose by scenario.
- **Agent Layer**: Team-type Skills (`/investment-team`, `/earnings-team`, etc.) run 4 master-perspective agents in parallel under a team lead — independently search and judge, challenge each other, consolidate at the end. Light Skills bypass this layer, calling tools directly.
- **Tools Layer**: Precise calculation, real-time web search, report audit — ensures all report data is rigorous and verifiable.

---

## Skills List (19 Skills)

### 🔬 Deep Research

| Skill | Purpose | When to Use |
|---|---|---|
| [`/investment-research`](skills/investment-research.md) | Integrated 4-Giant Analysis | 360-degree research of public company |
| [`/investment-team`](skills/investment-team.md) | Multi-Agent Parallel Research Team | 4 agents in parallel — fastest and most comprehensive |
| [`/management-deep-dive`](skills/management-deep-dive.md) | Deep Dive on Management | "Buying stock is buying people" — when management is the key variable |
| [`/private-company-research`](skills/private-company-research.md) | Private Company Research | Research of information-sparse private companies like Ant Group, SpaceX |
| [`/deep-company-series`](skills/deep-company-series.md) | 8-Part Deep Dive Series | Publication-quality series, ~120k characters from cognitive reset to decision convergence |

### 📊 Earnings Analysis

| Skill | Purpose | When to Use |
|---|---|---|
| [`/earnings-review`](skills/earnings-review.md) | Deep Read of Earnings (Primary Documents) | Like Buffett reads reports — only raw disclosure documents, no sell-side reports |
| [`/earnings-team`](skills/earnings-team.md) | Earnings Team + Publishable Articles | 4 giants interpret earnings in parallel → editorial polish → reader review → publication-ready |

### 🏭 Industry Screening

| Skill | Purpose | When to Use |
|---|---|---|
| [`/industry-research`](skills/industry-research.md) | Industry Value Chain Scan | Map investment opportunities across entire value chain of an industry |
| [`/industry-funnel`](skills/industry-funnel.md) | Industry Funnel Screening | Total market → Pre-screening ≤10 companies → Final selection 3 companies with deep analysis |
| [`/quality-screen`](skills/quality-screen.md) | Quality Screen (7 Rigorous Metrics) | Quickly eliminate non-elite companies; supports batch screening for individual ticker/industry/index/theme |
| [`/bottleneck-hunter`](skills/bottleneck-hunter.md) | Supply Chain Bottleneck Hunter | From big trends, find physical supply chain bottlenecks and arbitrage opportunities |
| [`/investment-checklist`](skills/investment-checklist.md) | Buffett Pre-Purchase Checklist | 6 gates, 10 minutes to determine if worth deep research |

### 📈 Portfolio Management

| Skill | Purpose | When to Use |
|---|---|---|
| [`/portfolio-review`](skills/portfolio-review.md) | Portfolio Review & Optimization | From "researching companies" to "managing portfolio" — position sizing, concentration, rebalancing |
| [`/thesis-tracker`](skills/thesis-tracker.md) | Investment Thesis Tracker | Post-purchase discipline system: continuously track if investment thesis is being invalidated |
| [`/thesis-drift`](skills/thesis-drift.md) | Thesis Drift Detection | Compare 2 theses/reports, distinguish fact change vs. valuation change vs. language change |
| [`/news-pulse`](skills/news-pulse.md) | Quick Price Movement Factor Analysis | When stock spikes/crashes — 10 minutes to clarify |

### 🧠 Thinking Tools

| Skill | Purpose | When to Use |
|---|---|---|
| [`/dyp-ask`](skills/dyp-ask.md) | Duan Yongping Q&A | Think about any question using Duan Yongping methodology — business, investing, life |
| [`/financial-data`](skills/financial-data.md) | Financial Data Retrieval & Cross-Validation | Ensure critical data comes from 2+ independent sources; alert on discrepancies >1% |
| [`/wechat-article`](skills/wechat-article.md) | WeChat Article Workflow | Author, editor, and reader agents collaborate to produce publication-ready articles |

---

## Quick Start

### Cost and Model Selection

Deep research Skills, by design, execute multiple research passes, multi-source validation, and multi-agent integration, which can consume tokens in volume. That cost is part of covering business quality, financials, industry structure, and risk more comprehensively.

For significant investment decisions, the maintainer's view is that typically the most powerful model delivers best analysis ROI; saving model cost shouldn't sacrifice critical decision quality. Light models are useful for triage, summarization, and low-risk questions, but moat-valuation-management-risk integration should be considered as depending more heavily on model capability.

To reduce costs, adjust workflow before trying to cheapen deep research itself: first use [`/quality-screen`](skills/quality-screen.md) to eliminate weak companies, or [`/news-pulse`](skills/news-pulse.md) for quick price movement analysis. Only execute [`/investment-research`](skills/investment-research.md) or [`/investment-team`](skills/investment-team.md) if result deserves deep research.

### 1. Install AI Client

This repository maintains one standard workflow and provides both Claude Code commands and Codex skills. Install the client you use.

For Claude Code users:

```bash
npm install -g @anthropic-ai/claude-code
```

For Codex users on macOS / Linux:

```bash
# macOS / Linux
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# or use npm
npm install -g @openai/codex

# or use Homebrew
brew install --cask codex

# Verify installation
codex --version
```

Windows users can use the official PowerShell installer: `powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"`

If `codex --version` displays version, proceed to install Codex skills from this project.

#### Reduce Approval Prompts

These Skills make many tool calls, and Claude Code will request approval by default for each. This behavior comes from Claude Code's client-side permission system, not repository default settings this project can change.

If you trust the current workflow and are running in a trusted environment, you can launch Claude Code in permission-skip mode:

```bash
claude --dangerously-skip-permissions
```

Warning: This mode disables Claude Code's tool approval guardrails. Only use if you trust the repository, commands, and working directory.

### 2. Install Skills

For Claude Code users on macOS / Linux:

```bash
# Clone repository
git clone https://github.com/xbtlin/ai-berkshire.git

# Copy skills to Claude Code global commands directory
cd ai-berkshire
./scripts/install-claude-commands.sh
```

For Claude Code users on Windows PowerShell / Command Prompt:

```bat
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire
.\scripts\install-claude-commands.bat
```

For Codex users on macOS / Linux:

```bash
# Clone repository
git clone https://github.com/xbtlin/ai-berkshire.git

# Generate and install Codex skills to ~/.codex/skills
cd ai-berkshire
./scripts/install-codex-skills.sh

# Optional: Install Codex slash prompts to ~/.codex/prompts
# If you want to use /investment-research entry points like Claude Code
./scripts/install-codex-prompts.sh
```

For Codex users on Windows PowerShell / Command Prompt:

```bat
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire
.\scripts\install-codex-skills.bat

REM Optional: Install Codex slash prompts
.\scripts\install-codex-prompts.bat
```

The repository maintains 3 entry points: `skills/*.md` are the source for Claude Code commands; `codex-skills/*/SKILL.md` are Codex skill packages that `scripts/sync-codex-skills.py` generates from `skills/*.md`; `codex-prompts/*.md` is an optional Codex slash prompt compatibility layer.

### 3. How to Use

Call directly in Claude Code:

```bash
# Deep research
/investment-research Tencent
/investment-team Meituan
/management-deep-dive Zhang Xiaolong, Meituan
/private-company-research SpaceX
/deep-company-series Pinduoduo

# Earnings analysis
/earnings-review Tencent 2025Q4
/earnings-team PDD 2025 Annual

# Industry screening
/industry-research Nuclear Power
/industry-funnel AI Computing
/quality-screen Hang Seng Index Constituents
/bottleneck-hunter AI Infrastructure
/investment-checklist Kweichow Moutai, NVIDIA, Apple

# Portfolio management
/portfolio-review Tencent 30%, Meituan 20%, Kweichow Moutai 20%, Cash 30%
/thesis-tracker Pinduoduo
/thesis-drift Pinduoduo reports/pinduoduo-thesis-2025Q4.md reports/pinduoduo-thesis-2026Q1.md
/news-pulse Tencent

# Thinking tools
/dyp-ask Where is Pinduoduo's true moat?
/wechat-article Meituan
```

After installing in Codex, restart Codex and reference by skill name:

```text
Use investment-research to research Tencent
Use earnings-review to analyze 2025 annual earnings PDD
Use industry-funnel to screen AI Computing
Use bottleneck-hunter to scan AI Infrastructure bottlenecks
Use thesis-drift to compare 2 Pinduoduo investment theses
Use wechat-article to write Meituan investment article
```

If you installed Codex slash prompts, restart Codex and search from `/` menu. Official Codex custom prompt entry points typically appear as `prompts:<name>`:

```text
/prompts:investment-research Tencent
```

---

## Detailed Skill Explanation

### 1. `/investment-research` — Integrated 4-Giant Analysis

The most thorough single-company deep research framework. Executes 7 modules in sequence:

```
Data Collection → Business Essence (Duan Yongping) → Moat (Buffett) → Reverse Thinking (Munger)
    → Management Evaluation (Duan Yongping + Buffett) → Civilizational Trend (Li Lu)
    → Valuation & Safety Margin
```

**Key Features**:
- AI Research Bias Recognition Mechanism (A/B/C Information Richness Assessment)
- Multi-Source Cross-Validation of Critical Data (Manual market cap calculation, 2+ independent sources)
- "Follow-up Questions" from each giant woven throughout
- 3-Scenario Valuation (Bull/Base/Bear) + Reverse DCF

**Output Sample**:

> #### Integrated Judgment Memo
>
> | Dimension | Conclusion | Confidence |
> |---|---|---|
> | Business Quality (Duan Yongping) | Excellent: Platform business, bidirectional network effects, marginal cost near zero | ★★★★★ |
> | Moat (Buffett) | Wide and Expanding: Network effects + Switching costs + Economies of scale, triple layer | ★★★★☆ |
> | Management (Duan Yongping + Buffett) | Strong: Founder-led, excellent capital allocation discipline | ★★★★☆ |
> | Maximum Risk (Munger) | Policy regulation uncertainty; new business losses suffocate total profit | ★★★☆☆ |
> | Civilizational Trend (Li Lu) | Aligned with digital consumption trend, but not "civilizational paradigm shift" | ★★★★☆ |
> | Valuation (Buffett + Duan Yongping) | Current P/E 18x, slightly below historical median, modest safety margin | ★★★★☆ |
>
> **Duan Yongping**: "The essence of this business is connecting consumers and merchants — profit from efficiency. Excellent business characteristics: more users → more merchants, more merchants → more users. Once the flywheel starts spinning, it's extremely hard to stop."
>
> **Munger**: "Always reverse, always reverse — if this company disappeared tomorrow, what would merchants and users do? If the answer is 'find a substitute quickly', the moat isn't deep enough. If the answer is 'life very inconvenient', that's worth paying attention to."

---

## Real Research Reports

> Below are real investment research reports generated by this framework. They demonstrate actual quality of AI-driven research output.

| Company | Skill Used | Core Conclusion | Report |
|---|---|---|---|
| Pinduoduo (PDD) | `/investment-team` | Score 3.4/5 — Extremely cheap but 10-year certainty insufficient; appropriate for moderate position | [View Report](reports/pinduoduo/) |
| Tencent (0700.HK) | `/investment-research` | Social Monopoly + Excellent Capital Allocation; Forward P/E 14x is Fair to Low | [View Report](reports/tencent/) |
| 7-Company Comparison | `/investment-checklist` | Kweichow Moutai & Tencent Pass; NVIDIA, Meituan & Kuaishou Conditional; Pinduoduo & Pop Mart Gray | [View Report](reports/multi-company-checklist-20260408.md) |
| Master Holdings Tracker | Custom Research | Latest 13F Holdings of Buffett / Li Lu / Duan Yongping + PDD Cost-Basis Analysis | [View Report](reports/master-holdings-tracker-20260408.md) |

---

## Design Philosophy

### Integration of 4-Giant Methodology

**Duan Yongping · "Correct Business"** — The essence of business. Common starting point of 3 other perspectives:

| Buffett | Munger | Li Lu |
|:---:|:---:|:---:|
| Moat<br>Safety Margin<br>Management | Reverse Thinking<br>Risk List<br>Bias Audit | Civilizational Trend<br>Paradigm Shift<br>Industry Value |

The 4 giants are not merely dividing labor — **they're designed to challenge each other**:
- If Duan Yongping says "excellent business" → Munger asks "how could it collapse?"
- If Buffett says "cheap enough" → Li Lu asks "will it exist in 10 years?"
- Not pasting 4 reports — it's **collision of 4 thinking systems**

### Financial Precision Tool (`tools/financial_rigor.py`)

| Functionality | Command | Problem It Solves |
|---|---|---|
| **Market Cap Verification** | `verify-market-cap` | Price × Shares Outstanding, precise calculation, unit error detection |
| **Valuation Verification** | `verify-valuation` | P/E / P/B / ROE / FCF Yield — rigorous decimal arithmetic |
| **Multi-Source Cross-Validation** | `cross-validate` | Auto-compare same data point across N sources; alert on discrepancies beyond range |
| **3-Scenario Valuation** | `three-scenario` | Precise Bull/Base/Bear target price calculation |
| **Benford's Law Detection** | `benford` | Detect anomalies in first-digit distribution of financial data |
| **Precision Calculator** | `calc` | Calculate any financial formula with precision — replace LLM arithmetic |

**Design Principle**: All calculations use Python `decimal.Decimal` (precise decimal arithmetic), never `float` (floating-point approximation). In financial context, `0.1 + 0.2 = 0.3` must never fail.

---

## Future Direction

- [ ] Historical Backtest: AI Research Reports vs. Actual Stock Price Performance
- [ ] Macroeconomic Cycle Analysis Framework
- [ ] Real-time Data Feed through MCP (Wind / Bloomberg / Yahoo Finance)

---

## Disclaimer

This project is for educational and research purposes only, and does not constitute investment advice. Investments involve risk; exercise judicious judgment. Always conduct your own due diligence (DYOR).

---

## License

MIT License

---

> "The best investment you can make is in yourself." — Warren Buffett
>
> AI Berkshire: For everyone to have their own investment research team.

## Star History

If this project was useful to you, please give it a star!

[![Star History Chart](https://api.star-history.com/svg?repos=xbtlin/ai-berkshire&type=Date)](https://star-history.com/#xbtlin/ai-berkshire&Date)
