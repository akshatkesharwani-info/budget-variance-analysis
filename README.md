# Budget Variance Analysis

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Cost](https://img.shields.io/badge/Cost-Free%20(Google%20Colab)-orange)
![Data](https://img.shields.io/badge/Data-Simulated-lightgrey)

A budget vs actual variance report by department, cost category and month, with an Excel output and a run-rate forecast.

## Table of Contents
1. [Problem Statement](#problem-statement)
2. [STAR Summary](#star-summary)
3. [Dataset](#dataset)
4. [What the Notebook Does](#what-the-notebook-does)
5. [Key Results (from the executed run)](#key-results-from-the-executed-run)
6. [Sample Output](#sample-output)
7. [Checks and Fallbacks](#checks-and-fallbacks)
8. [Limitations](#limitations)
9. [Tech Stack](#tech-stack)
10. [How to Run](#how-to-run)
11. [Files](#files)
12. [About Me](#about-me)

## Problem Statement
A company sets a budget for each department at the start of the year. Every month, finance needs to know where actual spend went above or below plan, which departments and cost categories cause the biggest gaps, and where the year is heading if the current trend continues.

## STAR Summary
- **Situation:** Department budgets existed, but there was no single view of where spending drifted from plan.
- **Task:** Build a variance report that separates favorable from unfavorable variance and flags the problem areas.
- **Action:** Calculated variance (amount and %) for 288 monthly line items across 6 departments and 4 cost categories, flagged items more than 10% away from budget, built department, category, heatmap and year-to-date views, and forecast year end spend from the last 3 closed months.
- **Result:** Total actual spend was 5.1% above budget (599,345). Marketing was the largest overspender at 16.0%, 95 of 288 line items were flagged, and the run-rate forecast pointed to a 3.49% overrun.

## Dataset
- **Simulated data created inside the notebook** (fixed random seed), not real company data. It contains 288 rows: 6 departments x 4 categories x 12 months (2025).
- Columns: Month, Department, Category, Budget, Actual.
- Some overspending patterns were deliberately built in (for example Marketing and IT overspend, and a Travel spike in some months), so the findings show that the method detects them. They are not claims about a real company.

## What the Notebook Does
1. Creates the budget vs actual dataset.
2. Calculates Variance = Actual - Budget and Variance % (for expenses, above budget = Unfavorable).
3. Flags line items more than 10% off budget.
4. Summarises variance by department and by category.
5. Draws a department x month variance heatmap, the monthly trend and year-to-date variance.
6. Lists the top 10 overspends and top 5 savings.
7. Forecasts year end spend (Jan to Sep treated as closed, Q4 forecast from the average of the last 3 closed months).
8. Saves an Excel report with 6 sheets.

## Key Results (from the executed run)
| Metric | Value |
|---|---|
| Total budget / total actual | 11,748,480 / 12,347,825 |
| Total variance | +599,345 (5.1%) |
| Line items flagged (more than 10% off budget) | 95 of 288 |
| Marketing variance | +324,527 (16.02%) |
| IT / Sales / Operations | +8.47% / +4.66% / +2.09% |
| Finance / HR (under budget) | -2.90% / -4.48% |
| Category with highest overrun | Travel (+12.71%) |
| Biggest single line | Marketing - Salaries (+132,560, 13.1%) |
| Highest % line in top 10 | Marketing - Travel (+23.7%) and Marketing - Vendor Services (+23.1%) |
| Forecast year end spend vs budget | 12,157,920 vs 11,748,480 (+409,440, 3.49%) |
| Forecast overrun by department | Marketing 12.9%, IT 5.7%, Sales 3.6%, Operations 0.7% |

August 2025 was the only month where total actual spend was below budget (-2,632).

## Sample Output
```
KEY INSIGHTS
--------------------------------------------------
1. Total actual spend is 5.1 % above the total budget (gap = 599345.0 )
2. Biggest overspending department: Marketing ( 16.0 % over budget )
3. Most under budget department: HR ( -4.5 % )
4. Category with highest overrun: Travel ( 12.7 % )
5. Single biggest problem line: Marketing - Salaries ( 132560.0 over )
6. 95 of 288 monthly line items are more than 10% away from budget
7. If the trend continues the year will end 409440.0 over budget
```

## Checks and Fallbacks
- The sign convention is explicit: positive variance on an expense is Unfavorable.
- The 10% flag threshold is applied at monthly line-item level and counted (95 of 288).
- The forecast is a simple run-rate method and is labelled as such. It is not a statistical model.
- Data is generated with a fixed seed, so the numbers above repeat on every run.
- No LLM or paid API is used, so there is no cost or latency to track.

## Limitations
- The data is simulated, so the department rankings come from the settings used to generate it.
- The forecast treats Jan to Sep as closed and does not model seasonality.
- The notebook does not compare the Q4 forecast with the simulated Q4 actuals.

## Tech Stack
| Area | Tools |
|---|---|
| Language | Python |
| Data handling | pandas, numpy |
| Charts | matplotlib, seaborn |
| Excel output | openpyxl |
| Environment | Google Colab |

## How to Run
1. Open `budget_variance_analysis.ipynb` in Google Colab.
2. Click Runtime > Run all.
3. No dataset download or API key is needed.
4. The charts and `budget_variance_report.xlsx` are saved in the Colab file panel.

## Files
- `budget_variance_analysis.ipynb` (executed notebook with outputs)
- `requirements.txt`
- Generated by the notebook: `variance_by_department.png`, `budget_vs_actual_by_category.png`, `variance_heatmap.png`, `monthly_trend.png`, `ytd_variance.png`, `budget_variance_report.xlsx`

## About Me
**Akshat Kesharwani** | Data Analyst and Data Scientist (fresher) | Sagar, Madhya Pradesh
- Portfolio: https://akshatkesharwani-info.github.io/
- GitHub: https://github.com/akshatkesharwani-info
- Email: akshatkesharwani12345@gmail.com
