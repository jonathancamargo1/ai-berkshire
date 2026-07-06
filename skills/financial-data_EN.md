# Financial Data Acquisition and Cross-Validation Standard

This standard applies to all research involving corporate financial data. **Every key data point must come from two independent sources, deviations >1% must be flagged.**

---

## Data Source Priority Hierarchy

### US Stocks (PDD, Tencent ADR, NetEase ADR etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **macrotrends** | macrotrends.net/stocks/charts/{ticker} | Direct access, no registration |
| 2 (Secondary) | **stockanalysis** | stockanalysis.com/stocks/{ticker}/financials | Direct access, no registration |
| Original Primary | SEC EDGAR | sec.gov/cgi-bin/browse-edgar | 10-K / 10-Q original text |

### Hong Kong Stocks (Tencent 0700, NetEase 9999, Meituan 3690 etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **aastocks** | aastocks.com/tc/stocks/analysis/company-fundamental | Direct access |
| 2 (Secondary) | **macrotrends** (ADR code) | Tencent uses TCEHY, NetEase uses NTES | Direct access |
| Original Primary | HKEx Disclosure | hkexnews.hk | Annual Report PDF |

### China A-Shares (37 Interactive, Gibbit etc.)

| Priority | Source | URL | Acquisition Method |
|--------|------|-----|----------|
| 1 (Primary) | **Eastmoney** | eastmoney.com → search code → Financial Tables | Direct access |
| 2 (Secondary) | **Juchai** | cninfo.com.cn | Original Annual/Quarterly PDF |

---

## Execution Standard

### First Step: Obtain Data

For each financial indicator (revenue, net profit, gross margin, operating cash flow, leverage ratio etc.), separately obtain data from **source 1** and **source 2**.

### Second Step: Deviation Calculation and Flagging

```
Deviation Rate = |Source 1 Value - Source 2 Value| / Source 1 Value × 100%
```

| Deviation | Processing Method |
|------|----------|
| ≤ 1% | ✅ Consistent, use source 1 value, flag both sources |
| 1% ~ 5% | ⚠️ Flag "data variance exists", note both values, explain possible cause (exchange rate/accounting method) |
| > 5% | ❌ Flag "significant data variance", must verify against original report before using |

### Third Step: Data Presentation Format

Every key data point must be annotated as follows:

```
Revenue: $1.239 billion ✅
  - macrotrends: $1.241 billion
  - stockanalysis: $1.237 billion
  - Deviation: 0.3%
```

Variance Example:
```
Net Profit: $245 billion ⚠️ Data Variance Exists
  - macrotrends: $245 billion (GAAP)
  - stockanalysis: $278 billion (Non-GAAP)
  - Deviation: 13.5% — Reason: Different accounting method (GAAP vs Non-GAAP)
```

---

## Common Variance Reasons (Not Necessarily Data Errors)

| Reason | Explanation |
|------|------|
| GAAP vs Non-GAAP | Most common, especially for profit data |
| Exchange Rate Conversion | Hong Kong$/RMB/USD different timing |
| Fiscal Year Definition | Calendar year vs Fiscal year (e.g., Apple ends October) |
| Consolidation Scope | Include minority shareholders? |
| Update Lag | Platform hasn't updated latest period yet |

---

## Special Rules

1. **Unlisted Companies** (miHoYo, Lilith etc.): With only one data source, mark `[Estimated]` before data, do not perform cross-validation
2. **Quarterly vs Annual Data**: Prefer using annual data for cross-validation, some platforms may have quarterly lag
3. **Original Report Priority**: If both sources differ from original report (10-K/Annual PDF), use original report as correct, flag source error

---

## Quick Index

| Scenario | Primary Source | Backup Source |
|------|---------|----------|
| PDD / Pinduoduo | macrotrends.net/stocks/charts/PDD | stockanalysis.com/stocks/pdd |
| Tencent | macrotrends.net/stocks/charts/TCEHY | aastocks（0700.HK） |
| NetEase | macrotrends.net/stocks/charts/NTES | aastocks（9999.HK） |
| 37 Interactive | eastmoney.com（002555） | cninfo.com.cn |
| Gibbit | eastmoney.com（603444） | cninfo.com.cn |
| Nintendo | macrotrends.net/stocks/charts/NTDOY | stockanalysis.com/stocks/ntdoy |
| Capcom | macrotrends（CCOEY） | stockanalysis（CCOEY） |