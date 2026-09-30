**Short-term monitoring · Medium-term testing · Long-term testing**

A bilingual (English/Chinese) practitioner handbook covering VaR, Expected Shortfall, backtesting, stress testing, drawdown and scenario analysis. It maps each topic to **AIFMD, UCITS and MiFID II** requirements, and every calculation can be reproduced in Python.

> Regulatory content is current as of **30 September 2026**. These are study notes, not investment, legal or compliance advice.

---

## Contents

| Part | Chapters | Topics |
|---|---|---|
| **I. Short-term monitoring** (1 day – 1 month) | 1–9 | <ul><li>VaR as a percentile; ES derivation</li><li>Volatility: EWMA, GARCH</li><li>Historical and filtered historical simulation</li><li>Cornish–Fisher and EVT</li><li>Parametric vs historical vs Monte Carlo VaR</li><li>Component and multi-factor VaR</li><li>Yield curves</li><li>Backtesting: Kupiec, Christoffersen, traffic lights</li><li>UCITS global exposure and the commitment approach</li><li>Counterparty risk and CVA</li></ul> |
| **II. Medium-term testing** (weeks – 1 year) | 10–12 | <ul><li>Stress-test types</li><li>Taylor expansion vs full revaluation (options, barriers)</li><li>Conditional and reverse stress tests</li><li>Liquidity stress testing and liquidity management tools (LMTs)</li></ul> |
| **III. Long-term testing** (1 year +) | 13–15 | <ul><li>Drawdown theory and drawdown limits</li><li>Multi-year scenario analysis</li><li>PRIIPs performance scenarios</li><li>Climate scenarios</li></ul> |
| **Practice** | 16–18 | <ul><li>Integrated three-horizon framework and checklist</li><li>AIFMD Annex IV reporting, step by step</li><li>Derivative-heavy funds: leverage bases, Greeks, margin liquidity, CSA terms and thresholds, collateral coverage</li></ul> |
| **Appendices** | A–C | <ul><li>Python reference implementation</li><li>Excel formulas</li><li>Bilingual glossary</li></ul> |

- **16 worked examples** with full numbers, plus **11 figures**
- **Regulatory mapping**: every chapter covers UCITS, AIFMD and MiFID II, with Basel/FRTB, EMIR and PRIIPs where relevant
- **S&P 500 case studies**: include an exact replication of a 99%/10-day VaR backtest (1,219 comparisons, 25 breaches)

## Repository layout

```
├── Market_Risk_Handbook.pdf          # English edition
├── src/                               # handbook source (HTML + KaTeX)
├── build.js / build_en.js             # render the PDFs with headless Chromium
├── var_toolkit.py                     # reusable functions: VaR, backtests, stress, drawdown
├── analysis.py / analysis2.py         # reproduce all figures and case-study numbers
├── sp500.csv                          # S&P 500 closing levels, Jan 2013 – Jan 2018
└── *.png                              # generated figures
```

## Reproduce

**Requirements**
- Python 3.10+ with `numpy`, `pandas`, `scipy`, `matplotlib`
- Node 18+ with `playwright` and `katex`
- CJK fonts (Noto Serif/Sans CJK SC) for PDF rendering

```bash
pip install numpy pandas scipy matplotlib
npm install playwright katex

python var_toolkit.py      # backtests, reverse stress test, drawdown statistics
python analysis.py         # Part I figures and VaR model comparison
python analysis2.py        # Parts II–III: stress tests, drawdown Monte Carlo, scenarios

node build.js              # Chinese edition
node build_en.js           # English edition
```

> `build*.js` loads Playwright from a global path. If you install it locally, change the `require(...)` line to `require('playwright')`.

## Data and third-party material

`sp500.csv` holds S&P 500 index closing levels, used for illustration only. Check your data licence before redistributing index data. Stress shocks and scenario paths are labelled as illustrative in the text; they are not forecasts.

## Author

**Yini Gao** · [LinkedIn](https://www.linkedin.com/in/yinigao) · [GitHub](https://github.com/YiniG)

## License

Text and figures: CC BY-NC 4.0 · Code: MIT *(adjust as preferred)*

