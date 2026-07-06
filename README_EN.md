English | [中文](README.md) | [Português](README_PT.md) | [日本語](README_JA.md)

[![GitHub Trending](https://trendshift.io/api/badge/repositories/63696)](https://trendshift.io/repositories/63696)

# AI Berkshire - Value Investing Research Framework for the AI Era

> "Price is what you pay, value is what you get." — Warren Buffett
>
> Redefine the depth and efficiency of investment research with AI.

**AI Berkshire** is a comprehensive suite of investment research Skills compatible with both Claude Code and Codex, systematizing and structuring the methodologies of four value investing masters — Warren Buffett, Charlie Munger, Tan Yongping, and Li Lu — to deliver professional-grade investment research through AI Agents.

One person + Claude Code / Codex = a professional investment research team.

[Real Track Record](#real-track-record) · [Why You Can't Ask AI Directly](#why-you-cant-ask-ai-directly) · [Skills Overview](#skills-overview19-skills) · [Quick Start](#quick-start) · [Real-World Reports](#real-world-research-reports) · [Design Philosophy](#design-philosophy) · [Public Channel](#featured-research-launches-on-our-public-channel)

---

## Real Track Record

> Not just theory. This framework is backed by a proven investment system verified with real capital.

### 2024 Full-Year Return: +69.29%

<img src="assets/2024-returns.jpg" width="300" />

### 2025 Full-Year Return: +66.38%

<img src="assets/2025-returns.jpg" width="300" />

### Comparison with Major Indices

| Metric | 2024 Full Year | 2025 Full Year |
|--------|---|---|
| **This Framework (Actual)** | **+69.29%** | **+66.38%** |
| Hang Seng Index | +17.67% | +27.77% |
| S&P 500 | +23.31% | +16.39% |
| CSI 300 | +14.68% | +17.66% |
| NASDAQ | +28.64% | +20.36% |

**2024 Outperformance**: Beat S&P 500 by **46 percentage points**, Hang Seng by **52 percentage points**

**2025 Outperformance**: Beat S&P 500 by **50 percentage points**, Hang Seng by **39 percentage points**

**Real P&L over two years exceeds 1.46 million**, consistently outperforming major global indices for two consecutive years.

> *Disclaimer: Historical returns do not indicate future performance. Screenshots are from real Futu Securities accounts.*

### Featured Research Launches on Our Public Channel

The repository contains the complete framework and all reports. Our public channel features **selections** — real in-depth research on companies that truly merit investment, plus my own judgment and decisions beyond what goes into formal reports:

<img src="assets/wechat-qr.png" width="160" alt="WeChat Public Account: 复利炼丹炉" />

**复利炼丹炉** —— Using AI to refine the investment research art.

---

## Why You Can't Ask AI Directly?

You can absolutely ask Claude directly: "Analyze whether PDD is worth buying". You'll get a "balanced" analysis with "on one hand... on the other hand..." ending with "investing has risk, judge for yourself".

**That analysis looks right, but won't help you make decisions.**

AI Berkshire doesn't solve "can it analyze", it solves the **quality of analysis and decision discipline**. Here are the core differences:

### 1. Forces Conclusions, No False Balance

Ask AI directly, you get both-sides hand-waving. AI Berkshire forces output: **Pass/Fail/Gray Zone**, with specific price ranges and layered recommendations.

> Typical AI answer: *"PDD has growth potential but also faces competitive pressure, investors need to weigh..."*
>
> AI Berkshire output:

> | Strategy | Recommendation | Price Range |
> |------|------|---------|
> | Aggressive | Can build 20% position here | $95-105 |
> | Conservative | Wait for buyback policy clarity | $85-95 |
> | Very Conservative | Fails 10-year certainty test, watch | — |
>
> **Mirror Test**: Can't explain in 5 sentences = Don't buy, no exceptions.

### 2. Four Master Perspectives in Conflict, Not Single Analysis

Not just "analyze using Buffett's method". Four viewpoints create **real contradictions and tension** —

Using PDD as an example:
- **Tan Yongping** (Business Model): Good business, C2M model hard to replicate → Score 3.7/5
- **Warren Buffett** (Financial Valuation): Discounted FCF PE only 6.3x, money printer → Score 4.4/5
- **Charlie Munger** (Inverse Thinking): Moat shallower than we think, Douyin hit 4 trillion GMV in 3 years → Score 3.5/5
- **Li Lu** (Long-term Certainty): Management culture has hidden risks, uncertain in 10 years → Score 2.0/5

**Buffett says "dirt cheap", Li Lu says "if uncertain don't buy"** — that conflict IS the true state of investment decision-making. A single prompt can't create this multi-perspective collision, and that collision is exactly what prevents blind spots.

### 3. Structured Bias-Prevention Mechanisms

What's most dangerous about AI isn't wrong answers, it's an answer that **looks bulletproof but crumbles under scrutiny**. AI Berkshire bakes multiple layers of "fraud detection" into the process:

| Mechanism | What Problem It Solves | Example |
|------|------------|------|
| **Citation Enforcement** | Hallucinations with no support | Require every claim cite source/year |
| **Inversion Test** | Confirmation bias | "Refute your own main argument" |
| **Inconsistency Check** | Contradictory logic | Compare conclusion vs analysis line-by-line |
| **Data Validation** | Calculation errors | Recalculate PE/ROE/FCF with Python |

---

## Skills Overview (19 Skills)

| Skill | Input | Output | Time |
|------|---------|--------|--------|
| `/investment-research` | Ticker symbol | Structured report (12 dimensions) | 8-12 min |
| `/investment-team` | Ticker symbol | 4 master perspectives + executive summary | 15-20 min |
| `/investment-checklist` | Ticker symbol | 50-point checklist (go/no-go) | 4-6 min |
| `/earnings-review` | Earnings call transcript | Earnings analysis (estimate vs actual) | 3-5 min |
| `/earnings-team` | Call transcript | 4 perspectives + public article | 8-10 min |
| `/management-deep-dive` | Ticker symbol | Deep management analysis (style, track record) | 6-8 min |
| `/thesis-tracker` | Company ID | Continuous thesis tracking over time | Ongoing |
| `/industry-research` | Sector/theme | Industry analysis, market size, dynamics | 8-12 min |
| `/industry-funnel` | N/A | Screening funnel: market → sector → company top-N | 10-15 min |
| `/portfolio-review` | Holdings list | Quarterly review, allocation, rebalancing | 5-8 min |
| `/private-company-research` | Name/description | Private company research (no public data) | 6-10 min |
| `/quality-screen` | Ticker | Quality filter: ROE >15%, debt <40%, debt-free | 2-3 min |
| `/news-pulse` | Company list | Weekly news summary + thesis impact | 3-5 min |
| `/bottleneck-hunter` | Company/sector | Identifies critical bottleneck, how to fix it | 4-6 min |
| `/dyp-ask` | Question | Tan Yongping's perspective on question | 2-3 min |
| `/financial-data` | Ticker | Structured extraction of key financial data | 1-2 min |
| `/thesis-drift` | Thesis ID | Detection: Is thesis still valid? Sell triggers | 3-4 min |
| `/deep-company-series` | Ticker | Deep multi-article series on company | 20-30 min |
| `/wechat-article` | Report | Transform technical report into public article | 2-3 min |

---

## Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire

# Install skills in Claude Code
bash scripts/install-claude-commands.sh

# OR install Codex prompts
bash scripts/install-codex-prompts.sh
bash scripts/install-codex-skills.sh
```

### First Use

```bash
# Use directly in Claude Code with /investment-research
/investment-research PDD

# OR use as Codex Prompt
# Copy prompt from codex-prompts/investment-research.md to your Codex
```

---

## Real-World Research Reports

> These aren't model outputs, but real research with real money at risk. Each report is audited by the investment strategy.

### Featured Reports (2025-2026)

- **Tencent Research** — Deep earnings analysis 2025Q4, sell recommendation
- **PDD Research** — Business model vs valuation, 4-master analysis
- **ADP Deep Dive** — Why an "AI-less software" is the safest money printer

### Complete Database

All reports in `reports/`. Each company has its folder with:
- 4-master analysis
- Thesis tracking
- Earnings analysis
- Management analysis

---

## Design Philosophy

### 1. Rigor Over Speed

> A wrong analysis fast is worse than right analysis slow.

- We don't trust LLM summaries — all data validated
- Requires sources for every claim — no hallucinations
- Acknowledges uncertainty instead of hiding it behind false confidence

### 2. Multiple Perspectives Beat Single Expertise

> You don't want an expert who agrees with you; you want a table of disagreement.

- 4 investment masters, different philosophies — **not harmony, contrast**
- Each perspective has its own pass/fail criteria
- The conflict between them is the most important signal

### 3. Treat Investing as Science, Not Art

> Measurable, replicable, auditable — or it's not investing, it's gambling.

- Every decision has clear entry/exit criteria
- Reasoning documented — not "market feeling"
- Track record auditable — to continuously improve process

### 4. Scalable Framework

> A system that only works for Warren Buffett isn't useful for you.

- Framework-agnostic — works for any market, sector, asset class
- Skills are composable — combine as needed
- Outputs are structured — machine-readable for automation

---

## Featured Research Launches on Our Public Channel

The featured social media account is **复利炼丹炉** on WeChat. First publishes:

- **Thematic Research** — Why is AI at an inflection point? Who benefits?
- **Opportunity Analysis** — Top 3 companies today by price tier
- **Portfolio Insights** — Quarterly rebalancing and reasoning

> Follow the account for:
> - Research insights ahead of the repository
> - Context beyond what goes into reports
> - Real-time market/macro discussion

---

## Contributing

Yes, we accept contributions. See `CONTRIBUTING.md`.

If you've done a solid 4-master analysis on a company — from a **truly divergent perspective, not copying** — open a PR.

---

## License

MIT License — open source and free to use. See `LICENSE`.

---

## Disclaimer

This framework is educational. No report is an investment recommendation. Do your own research, always.

> "On Wall Street, the herd is rewarded. But the money is made by those who think different." — Mark Spiegel
