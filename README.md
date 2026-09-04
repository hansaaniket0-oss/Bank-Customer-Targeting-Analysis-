# Bank Marketing Campaign — Customer Targeting & Contact Strategy Analysis

An end-to-end data analytics and business intelligence project analyzing a real
bank telemarketing campaign to identify high-value customer segments, optimize
contact strategy, and translate findings into an actionable targeting
recommendation.

---

## Executive Summary
This project analyzes **41,188 real customer contact records** from a
Portuguese bank's term deposit telemarketing campaign. By auditing disguised
missing data and validating cleaning decisions against actual conversion
evidence, this pipeline isolates the customer segments and contact strategies
that drive subscription — surfacing a segment converting at **65.38%**, nearly
6x the campaign baseline — and delivers a concrete targeting recommendation a
marketing team could act on directly.

---

## Tech Stack
- **Data Engineering / ETL:** Python (`pandas`, `numpy`)
- **Exploratory Data Analysis:** Python (`matplotlib`, `seaborn`)
- **Statistical Analysis:** Correlation analysis, multicollinearity checks, IQR-based outlier detection
- **Data Visualization & BI:** Power BI Desktop (DAX Measures, Data Modeling, Custom KPI Cards, Matrix Heatmaps)
- **Notebook:** Jupyter

---

## Business Key Performance Indicators (KPIs)

| Metric | Value | Business Relevance |
| :--- | :--- | :--- |
| **Overall Subscribe Rate** | **11.28%** | Campaign-wide baseline conversion rate |
| **Total Customers Contacted** | **39,861** | Audited record count after cleaning |
| **Previous Campaign Success Rate** | **65.38%** | Conversion rate among customers with a prior campaign success — the strongest signal found |
| **Average Contact Attempts** | **2.57** | Mean number of contacts per customer this campaign |

---

## Key Insights & Business Findings

1. **Data Quality — Disguised Missing Values, Not Blanket-Cleaned:**
   - 6 columns used `"unknown"` in place of real values (`default` affected ~21% of rows). Each column was tested individually against the baseline conversion rate rather than cleaned with one rule — `default`, `education`, and `marital` showed real signal and were kept as categories; `job`, `housing`, and `loan` showed negligible signal (unknowns converted within 0.5pp of baseline) and those rows were dropped, at a cost of only ~3.2% of the data.
   - Separately caught that `pdays` uses `999` as a placeholder for "never contacted" (96.3% of rows) — a value that would have silently corrupted any numeric analysis of that column if left untreated.

2. **Previous Campaign Outcome Is the Strongest Predictor:**
   - Customers whose previous campaign succeeded convert at **65.4%**, vs. **8.9%** for never-contacted customers and **13.9%** for previous failures — nearly 6x the overall baseline.

3. **Age Outperforms Marital Status and Education as a Segmentation Driver:**
   - The 60+ age band converts at **38–47%** across all marital statuses, while working-age bands (31–50) sit at **8–10%** regardless of marital status. Combined-segment testing showed "single" customers (14% overall) and certain education levels only appeared significant because they correlated with age/job — not independent effects.

4. **Repeated Contact Shows Sharply Diminishing, Then Negative, Returns:**
   - Subscribe rate falls from **13.0%** on the 1st contact attempt to **under 1%** past 20 attempts. Every one of the top 10 most-contacted customers (37–56 attempts) resulted in "no" — real evidence for a hard cap on repeat outreach, not just a soft guideline.

5. **Call Duration Deliberately Excluded from Targeting:**
   - Duration correlates with outcome (553s avg for "yes" vs. 221s for "no"), but it's only known after a call ends — unusable for deciding who to contact — and its extreme outliers were inconsistent (6 of the top 10 longest calls still resulted in "no").

---

<img width="931" height="524" alt="image" src="https://github.com/user-attachments/assets/a336e303-5c5a-48e9-bb60-46febd15395e" />
