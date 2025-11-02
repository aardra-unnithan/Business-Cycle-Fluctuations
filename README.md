##Overview

The project explores how economies and firms respond to major business cycle fluctuations, combining cross-country macroeconomic data and firm-level financial data from Compustat.

Part 1 – Cross-Country Analysis:
Compares cyclical patterns in the U.S., France, and Japan using quarterly macro data (2000–2023).
Key variables: GDP, unemployment, inflation, investment, and interest rates.
Methods: Hodrick–Prescott (HP) filter (λ = 1600), volatility measures, and cyclical correlations.

Part 2 – Country-Specific Analysis (Japan):
Event study of Japan’s Global Financial Crisis (2008–2009) and COVID-19 recession (2020).
Variables include GDP, investment, exports, unemployment, inflation, and business confidence.
Focus: severity, duration, and recovery speed of each downturn.

Part 3 – Firm-Level Analysis (Compustat):
Uses quarterly Compustat data (2005–2013) to analyze corporate responses to the GFC.
Indicators: revenue growth, capital expenditure intensity, leverage ratios, and profitability (ROA, ROE).
Comparison: manufacturing vs. services firms.

##Data Sources
Source	Description	Frequency	Access
FRED – Federal Reserve Bank of St. Louis	Real GDP, unemployment, inflation, and interest rate data for the U.S., France, Japan	Quarterly	https://fred.stlouisfed.org

OECD Data Explorer	CPI, business confidence, and export indicators	Quarterly	https://data.oecd.org

Compustat North America (via WRDS)	Firm-level financial statements	Quarterly (2005–2013)	

##Steps for Data Cleaning and Analysis

#Part 1 – Cross-Country Macroeconomic Analysis

Import macro data from FRED and OECD (real GDP, unemployment, CPI, investment, interest rates).

Convert all data to quarterly, seasonally adjusted where possible.

Apply Hodrick–Prescott filter (λ = 1600) to extract cyclical components.

Compute:

Volatility (standard deviation of HP cycles)

Correlation with GDP cycle (procyclicality)

Visualize GDP cycles and cross-country comparisons.

#Part 2 – Japan Event Study

Select event windows:

GFC: 2006Q3–2010Q4

COVID: 2018Q3–2021Q4

Index GDP, investment, and exports to 100 in the last pre-recession quarter.

Plot:

Real activity (GDP, investment, exports)

Unemployment

Inflation + Business Confidence

Compute metrics:

Peak-to-trough decline (%)

Quarters to trough and recovery

Average inflation and interest rates during recession.

#Part 3 – Firm-Level Compustat Analysis

Data: Compustat North America (Quarterly), 2005–2012.

Filters: Valid GVKEY and DATADATE; positive total assets; exclude financial firms (SIC 6000–6999).

Constructed indicators:

Revenue Growth = Δln(SALEQ)

Investment Rate = CAPX / ATQ

Leverage = (DLCQ + DLTTQ) / ATQ

Profitability (ROA) = NIQ / ATQ

Liquidity = CHEQ / ATQ

Data treatment: Winsorized at 1st–99th percentiles; medians used to represent typical firm.

Period tags:

Pre-GFC (2005–2007Q2)

During-GFC (2007Q3–2009Q4)

Post-GFC (2010–2012)

Aggregation: Median indicators computed for all firms and by sector (Manufacturing, Services, Other) and size (Small, Large).

Visualization: Multi-panel plots of firm indicators and sectoral differences.

Findings: Profitability and demand declined during the GFC; leverage rose; liquidity fell; investment remained flat; post-crisis recovery was slow and uneven.
