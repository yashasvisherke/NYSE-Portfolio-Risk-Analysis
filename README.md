# NYSE Portfolio Risk & Hedging Analysis

### [View Project Report & Findings (Notion)](https://www.notion.so/NYSE-New-York-Stock-Exchange-Portfolio-Risk-Hedging-Analysis-2965bbca764380579192f1b0cd6c0136?source=copy_link)

## Project Summary

This project analyzes over 850,000 rows of daily stock price data from the NYSE (2010-2016) to model and manage investment risk. The analysis moves from calculating individual stock volatility to building and testing multi-asset portfolios to find an optimal risk-reduction strategy.

---

## Tools Used
* **Python:** (Pandas, NumPy) for data manipulation and all calculations.
* **Notion:** For documenting key findings and project steps.
* **Power BI (WIP):** Currently developing a dashboard to visualize these findings.

---

## Key Findings & Methodology

### 1. Risk = Volatility (Standard Deviation)
* Calculated the daily returns for 500+ stocks.
* Determined that **risk** can be quantified as the **standard deviation of daily returns**.

### 2. The Hedging vs. Diversification Discovery
* Engineered a full **correlation matrix** to find assets that move in opposite directions.
* **Discovery:** True hedges (strong negative correlations) were nearly non-existent in this dataset.
* **Strategy Pivot:** Shifted from "hedging" to "diversification" by looking for assets with a **zero correlation (near 0.0)**.

### 3. The Two-Step Portfolio Test
* **Test 1 (The `EVHC` Trap):** Discovered that `EVHC` had a near-zero correlation to `AAPL` but was individually 2.5x riskier. This made the combined portfolio *more* volatile, proving that low correlation isn't enough.
* **Test 2 (Successful Diversification):** Modeled a 50/50 portfolio of `AAPL` (1.65% risk) and `ED` (0.97% risk). The final portfolio risk was **1.02%**, proving that diversification with a *low-risk, uncorrelated* asset successfully reduced total risk.

### 4. The True Hedge
* Scanned the entire 500x500 matrix to find the *best possible hedge* in the dataset.
* Found `FTV` and `MCK` (corr: -0.18).
* Proved that a 50/50 portfolio of these two assets (risk: 0.91%) was **safer than either stock individually** (1.33% and 1.52%), demonstrating the risk-subtracting power of a negative correlation.
