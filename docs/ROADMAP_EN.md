# ai-berkshire Roadmap

## P0: Short-term (1-2 months)

### A-Share Data Source Integration
- Integrate free data sources such as akshare and East Money
- Coverage of A-Share financial data, market quotes, and trading lists
- Existing Skills require no modification, only data layer expansion

## P1: Medium-term (3-6 months)

### HTML Report Output
- Add HTML report format alongside Markdown
- Support dark mode, navigation bar, and chart visualization
- Improve report dissemination and reading experience

### Multiple Depth Modes
- `lite`: Quick assessment in 5 minutes, providing valuation range and core conclusions
- `standard`: Current default mode, complete multi-agent research
- `deep`: Add more cross-validation and historical comparative analysis, institution-level depth

### Horizontal Comparison of Multiple Stocks
- Support horizontal comparison of 2-4 stocks on the same dimension
- Valuation benchmarking for same-sector companies
- Output comparison matrix and optimization recommendations

## P2: Long-term (6+ months)

### Test Coverage
- Add unit tests for core tools (financial_rigor.py, etc.)
- Add regression tests for Skill outputs
- Ensure iterations do not break existing functionality

### Portfolio-Level Analysis
- Evaluation of investment portfolio health
- Industry/geographic concentration analysis
- Correlation risk detection