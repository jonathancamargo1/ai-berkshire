---
name: deep-company-series
description: "AI Berkshire skill: Deep Company Series: Deconstructing One Company in 8 Long-Form Articles. Source: skills/deep-company-series.md."
---

## Codex adapter note

This skill is generated from `skills/deep-company-series.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Deep Company Series: Deconstructing One Company in 8 Long-Form Articles

Write an 8-article deep-dive series for $ARGUMENTS to be published on public channels like WeChat Official Accounts/Douyin. **The core IP is not "writing well", but "editing with rigor" — 99% of financial articles violate this skill's fact-checking standards**.

Reference sample: `reports/腾讯/《看懂腾讯》/`

---

## I. Trigger Scenarios

The user wants to produce "textbook-level" deep research on a company and publish it publicly in **long-form series format**. Distinct from a single report:
- 8 articles of ~120,000 characters total, from cognitive reset to complete decision-framework closure
- Each article stands independently (suitable for single-share), but threaded with one valuation/management/price judgment
- Written for "readers willing to spend 90 minutes understanding one company", not for sell-side clients

**Inappropriate scenarios for this skill**: single-report, earnings commentary, industry research — use instead `/investment-research`, `/earnings-review`, `/industry-research`.

---

## II. Series Template (8 Articles)

| # | Title Template | Core Question | Word Count |
|---|---------|---------|------|
| 01 | You Thought You Understood X, But You Didn't | Cognitive reset: break 3 common illusions | 4,000-5,000 |
| 02 | X's Moat—`<business essence in one sentence>` | How deep is the moat, does it persist in 5/10 years | 6,000-8,000 |
| 03 | X's Largest Profit Engine—`<most profitable business>` | What's the main business, why is it sustainable | 6,000-8,000 |
| 04 | Another Company Hidden on X's Books—`<hidden asset>` | Investment portfolio / subsidiaries / hidden value | 8,000-10,000 |
| 05 | In the AI Era (or Current Narrative), Is X a Winner or Loser | Epoch variable: decompose AI impact by business | 8,000-10,000 |
| 06 | Deconstructing X's Financials the Buffett Way | Financial depth: gross margin/FCF/ROE/SBC | 8,000-10,000 |
| 07 | `<Management Golden Quote>`—Is X's Management Worth Your Trust | Capital allocation discipline + integrity check + succession | 8,000-10,000 |
| 08 | How Much to Pay, What Signal Means Sell (Series Finale) | Three-scenario DCF + red-line checklist + position framework | 10,000-12,000 |

Add one `00-series-note.md` as table of contents, not for publication.

---

## III. Writing Style Standards

### Tone

- **Direct, sharp, no filler** — first sentence delivers numbers or contrarian conclusions
- **Value-investing framework** — Buffett/Munger/Duan Yongping/Li Lu perspectives woven in (but not piled)
- **No predetermined stance** — lay data first, deduce logic second, draw conclusions last
- **Present both sides** — every core judgment gets a "but on the other hand..." counterpoint
- **WeChat-native feel** — first 18-20 characters must stand alone (mobile preview)

### Forbidden Words

| Forbidden | Reason | Replacement |
|------|------|------|
| Obviously / Inevitably / Certainly | Subjective absolutism | Data shows / Evidence indicates |
| I think / I feel | Subjective tone | Delete or change to "per this framework" |
| Textbook-level / Divine touch | Traffic-seeker praise | Describe concrete facts |
| Severely misaligned / Severely undervalued | Strongly subjective words | Quote specific discount percentages |
| Perfect / Flawless | One-sided judgment | Add opposing-side observations |

### Title Style

- Use **contrasting numbers** or **contrarian conclusions** as hook ("7 failed attempts in 15 years", "Annual salary of 42.92M is only 0.0165% of profit")
- Subtitle neutral and descriptive ("—`<essential judgment>`")
- **Avoid traffic-seeker comparisons**: "mini-Buffett", "China's version of X", "YYDS" all banned
- Use terminology familiar to professional readers ("Berkshire" not "Buffett", company name over personal name)

---

## IV. Rigorous Fact-Check Checklist (Core IP)

### "False Precision" Traps to Watch Before Writing

1. **Probability-weighted expected value**: `30% × A + 50% × B + 20% × C = expected +X%` — this type of calculation is almost always garbage — probability allocation is pure subjectivity, creating false precision. **Only list scenarios + triggers + direction, don't calculate weighted expectations**.
2. **Third-party MAU/share measurements**: QuestMobile/Qimai/CBNData discrepancies are enormous (can differ 2-3× at same timepoint). **Use only the two most reliable for anchor, make the rest qualitative**.
3. **Linear extrapolation of historical growth**: `2025 +33% × 5-year compound → 2030 X` is financial-illiterate forecasting. **Scenario assumptions + high/low bands + not a promise**.
4. **Undisclosed stake percentages**: ByteDance, Halti-type unlisted companies **never disclose holdings**. **Give ranges, mark "unknowable"**.
5. **Strong attribution**: Competitor failure = because X. List multiple causes, **this piece does no single attribution**.

### 7 Mandatory Checks During Revision

```
□ 1. Cross-article number consistency: total market cap, Non-IFRS net profit, key stakes % aligned across series
□ 2. Methodology notation: Non-IFRS / GAAP / Non-IFRS-SBC / FCF which to use, clear throughout
□ 3. Double-counting sweep: already-consolidated subsidiaries not in "investment portfolio", SOTP not double-counted
□ 4. Horizontal comparison fairness: can't be "main business PE (excl. cash + portfolio)" vs "peer PE (unexcl.)"
□ 5. All probability-weighted expectations deleted: see above
□ 6. All absolutized statements weakened: grep "obviously|inevitably|severely|textbook|perfect"
□ 7. Third-party data source annotation: every non-financial-statement data point gets "(Source: X)" after
```

### Model Preferences

Before writing, **list already-known hard errors**:
- Historical return multiples: must use cumulative input basis (e.g., Riot 33× not 58×)
- Stake percentages: must check latest Futu/financial-statement (e.g., Tencent holds Meituan 1.5% not 6.4%)
- "Dividend distribution" accounting: treat as disposal gain under IFRIC 17 at declaration date (e.g., JD in 2021, Meituan in 2022 but small amount)
- Share count will bounce: SBC concentrated at year-start will spike share count short-term

---

## V. Execution Process

### Phase 1: Research (Complete Before Writing Articles 01-02)

1. Read company's last 5 years of annual reports, latest quarterly
2. Read at least 3 independent sell-side reports (find consensus + contrarian views)
3. Use `/investment-team` or `/investment-research` to generate internal research draft first
4. Confirm with user the 8 core thesis points (avoid discovering wrong direction after writing)

### Phase 2: Writing (Write 01→08 in order, no skipping)

- After completing each article, save to `reports/{company}/《Understanding {company}》/0X-XX.md`
- Don't push GitHub immediately — await user review
- After user revision feedback, revise
- After revision complete, git push

### Phase 3: Cross-Article Consistency Sweep (After all 8 complete)

Dispatch Explore agent to do parallel 8-article checks:
1. Same numbers (market cap, net profit, stake %) consistent across articles
2. Same terminology (FBS, SBC, Non-IFRS) explained on first appearance
3. Reference relationships: article 02 says "see details in article 06", does it actually map
4. Key-point recap vs main body, numbers match

### Phase 4: Final Pre-Publication Verification

```bash
# Must do local grep once before push (per ai-berkshire privacy rules)
grep -r "<local-username>\|/Users/\|<personal-identifying-info>" reports/ | head
```

Then `git pull --rebase && git commit && git push`.

---

## VI. Revision Feedback Processing

When user gives revision feedback, process in this order:

### 1. Verify Facts First (Don't Change Directly)

If user says "data X is wrong", first use Bash/Read to find original data and cross-verify:
- Check other earnings/financial reports in ai-berkshire for this company
- Check Futu/official disclosures
- Provide three-way comparison "what user said vs what I found vs what I used before"

### 2. Judge Revision Level

| Level | Type | Treatment |
|------|------|----------|
| 🔥 Hard error | Wrong numbers, wrong attribution, wrong methodology | Must change, no hesitation |
| ⚠️ Subjectivization | Strongly subjective words, absolutism, traffic-seeking comparisons | Weaken or delete |
| 🔬 Granularity | Source notation, methodology refinement | Low priority, balance with readability |
| ❓ Unreliable | Large third-party measurement disparities | **Delete is safer than change** (per clear user direction) |

### 3. Linked Checks After Revision

When changing one place, think "what else will reference this number/concept". E.g.:
- Changed total market cap → change PE / business PE / discount / FCF Yield across series
- Changed stake % → change TOP 10 ranking + historical stake table + reduction list
- Changed term methodology → change first definition + later references + key-point recap

### 4. Report Immediately After Push

```
Push successful (commit hash).
[N] revision summary total [with table]:
- What changed
- What linked-changed
- What hasn't changed yet

Awaiting next direction.
```

---

## VII. What This Skill Does NOT Do

- **Doesn't make investment decisions for readers** — all section endings have "not investment advice"
- **Doesn't predict stock price** — only provides "scenarios + triggers"
- **Doesn't calculate "expected annualized return" weighted value** — subjective probability allocation will mislead readers
- **Doesn't write "big X also holds"** — using others' stakes to endorse your judgment is anti-value-investing
- **Doesn't force all 8 articles** — if an article lacks enough independent content (e.g., management not particularly special), merge with others or reduce article count

---

## VIII. Compliance & Privacy

- All public reports **use only public information** (financial statements, official disclosures, sell-side reports, known third-party institutions)
- Don't use any **user personal information** (company codename, internal IM, undisclosed positions)
- Before push, grep local-username / `/Users/` / real names and other privacy fields
- Public attribution follows user's multi-layered identity strategy, don't mix

---

## One-Line Summary

**The core skill to write 'Understanding X Series' ≠ write well, but edit with rigor** —
89% of long-form financial pieces die from false-precision numbers, subjective probability-weighted expectations, absolutized claims. This skill exists to flag all these pits, avoid before writing, sweep clean after.