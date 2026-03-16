# Macroeconomic Drivers of Indian Sectoral Equity Returns (2014–2024)

A quantitative research project examining whether **RBI monetary policy (Repo Rate)** and **CPI inflation** can explain monthly equity returns across three NSE sectoral indices — NIFTY Bank, NIFTY IT, and NIFTY FMCG.

## Research Questions
1. Do changes in the RBI repo rate significantly affect sectoral equity returns?
2. Does CPI inflation have a statistically significant relationship with sector-level returns?
3. Which sector is most sensitive to monetary policy shocks?

## Dataset

| Source | Variable | Frequency |
|--------|----------|-----------|
| Yahoo Finance (`yfinance`) | NIFTY Bank, IT, FMCG adjusted closing prices | Monthly |
| Reserve Bank of India (RBI) | Repo Rate (LAF) | Event-driven → resampled monthly |
| Ministry of Statistics (MoSPI) | Consumer Price Index (CPI) | Monthly |

**Period:** January 2014 – December 2024  
**Returns:** Log monthly returns computed from adjusted closing prices  
**Inflation:** Year-on-year log CPI change

## Methodology

Three OLS regression models are estimated for each sector:

| Model | Specification | Purpose |
|-------|--------------|---------|
| Model 1 | Repo Rate (level) + Inflation | Baseline |
| Model 2 | ΔRepo Rate + Inflation | Preferred — markets react to changes |
| Model 3 | ΔRepo (t, t-1) + Inflation (t, t-1) | Tests lagged policy transmission |

Supplemented by **12-month rolling correlations** to capture time-varying macro-equity relationships.

## Key Findings

- **Low R² across all models** (<5%) — consistent with the Efficient Market Hypothesis; macro variables alone have limited predictive power over monthly returns
- **Rate changes outperform levels** — Model 2 consistently fits better than Model 1, confirming markets price policy changes, not absolute levels
- **NIFTY Bank is most rate-sensitive** — strongest negative response to repo rate hikes, consistent with net interest margin compression
- **NIFTY FMCG is most defensive** — lowest sensitivity to both monetary policy and inflation
- **NIFTY IT shows distinct inflation dynamics** — likely driven by USD/INR and global growth expectations
- **Relationships are time-varying** — rolling correlations shift meaningfully around COVID-19 (2020) and the 2022–23 rate hike cycle

## Project Structure
```
├── ecofinpro.ipynb                        # Main analysis notebook
├── cpi_888.xlsx                           # CPI data (MoSPI)
├── Major Monetary Policy Rates...xlsx     # RBI repo rate data
└── README.md

## Requirements
```bash
pip install yfinance pandas numpy matplotlib seaborn statsmodels openpyxl


## How to Run

1. Clone the repository
```bash
   git clone https://github.com/yourusername/ecofinpro.git
   cd ecofinpro
```
2. Install dependencies
```bash
   pip install -r requirements.txt
```
3. Place the two Excel data files in the root directory
4. Open and run `ecofinpro.ipynb` top to bottom

---

## Limitations & Future Work

- Global macro controls (Fed Funds Rate, Brent crude, VIX, INR/USD) are excluded
- OLS assumes linear, constant relationships — GARCH models could better handle volatility clustering
- Structural break tests (Chow test) around COVID-19 and 2022 rate hikes would strengthen the analysis
- Coverage can be extended to Auto, Pharma, and Metals sectors

