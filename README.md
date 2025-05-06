# Credit Data Analysis

## Table of Contents

- [Executive Summary](#executive-summary)  
- [Introduction & Objective](#introduction--objective)  
- [Data Description](#data-description)  
- [Methodology](#methodology)  
- [Python Analysis](#python-analysis)  
  - [Default Rate by Age Group](#default-rate-by-age-group)  
  - [Employment Status Distribution](#employment-status-distribution)  
  - [Interest Rate vs Credit Score](#interest-rate-vs-credit-score)  
  - [Average Loan Amount by Purpose](#average-loan-amount-by-purpose)  
- [R Analysis](#r-analysis)  
  - [Default Rate by Annual Income Band](#default-rate-by-annual-income-band)  
  - [Default Rate by Credit Score Band](#default-rate-by-credit-score-band)  
  - [Default Rate by Education Level](#default-rate-by-education-level)  
  - [Default Rate by Employment Status](#default-rate-by-employment-status)  
  - [Default Rate by Loan Purpose](#default-rate-by-loan-purpose)  
- [Conclusions & Recommendations](#conclusions--recommendations)  
- [Appendix](#appendix)  

---

## Executive Summary

The analysis of Austrian consumer-loan data reveals that borrowers aged 36–55 are the most creditworthy, thanks to stable incomes, savings buffers, and well-established credit histories. Younger borrowers, often balancing education and entry-level jobs, face higher volatility in earnings, while retirees rely on fixed pensions that may not keep pace with living expenses. Employment stability also plays a pivotal role: full-time professionals and retirees benefit from predictable cash flows and structured financial support, whereas students and part-time workers juggle irregular incomes, leading to higher default rates.

Credit score emerges as the strongest predictor of loan performance. Those with scores below 580 experience substantial lending costs and elevated default likelihood, while top-tier borrowers pay minimal interest and virtually never default. Income levels further stratify risk: borrowers earning below €24 k annually have limited reserves and face competing financial demands, while high earners leverage diversified revenue streams and greater savings.

Finally, the purpose of financing influences outcomes. Home improvement loans, secured by property value, exhibit lower loss severity, whereas car financing carries greater depreciation risk. Smaller consumer and education loans tend to be repaid quickly, but can spike in default if borrowers drop out of school or face unexpected life events.

These insights suggest that Austrian lenders should refine underwriting criteria, prioritize risk-based pricing aligned to credit score and income, and tailor product features—such as collateral requirements and loan tenors—to borrower profiles and loan purposes.

---

## Introduction & Objective

This report provides a descriptive exploration of default behavior among Austrian consumer-loan applicants. By dissecting borrower demographics, financial attributes, and loan characteristics, the objective is to pinpoint which segments pose elevated credit risk and why. The findings will inform Austrian lending practices, guiding interest-rate strategies, underwriting policies, and portfolio management to balance growth with robust risk controls.

---

## Data Description

The dataset consists of categorized Austrian consumer-loan records with the following attributes:

- **Demographics:** Age group (six bands), education level (three tiers), and employment status (seven categories).  
- **Financials:** Annual income band, credit score band, interest rate charged, and loan amount.  
- **Loan Details:** Purpose classification (Car, Education, Furniture/Appliances, Home improvement, Other).  
- **Outcome:** Indicator of default within 12 months.

All information is anonymized and aggregated into bands to maintain privacy while allowing granular subgroup analysis.

---

## Methodology

1. **Data Processing:** Clean and categorize borrower records in Python and R.  
2. **Default Rate Calculation:** Compute the proportion of defaults by demographic and financial group.  
3. **Visualization:** Use Matplotlib/Seaborn and ggplot2 to reveal patterns across borrower segments and loan types.  
4. **Contextual Analysis:** Interpret visual findings within Austria’s socio-economic landscape, including labor markets, household incomes, and regulatory frameworks.

---

## Python Analysis

### Default Rate by Age Group

![Default Rate by Age Group](default_rate_by_age_group.png)

Borrowers aged 18–25 show heightened sensitivity to economic fluctuations as they often balance part-time employment with educational expenses. The subsequent drop in defaults among 26–35 year-olds reflects increasing job stability and dual-income households, though this group still navigates first mortgages and child-related costs. In the 36–45 cohort, defaults tick up slightly as loan sizes peak for home purchases and vehicle upgrades. The lowest defaults in the 46–55 and 56–65 brackets coincide with peak earnings, substantial savings, and paid-down debts, which enhance repayment capacity. After retirement, fixed pensions strain against healthcare and living costs, driving a rebound in defaults for the 66–75 cohort.

### Employment Status Distribution

![Employment Status Distribution](employment_status_pie.png)

Full-time workers benefit from consistent salaries and employer-backed benefits, enabling reliable loan servicing. Retirees draw on regulated pensions and often receive family support for larger expenses, maintaining a default rate on par with salaried employees. Students rely on grants, part-time jobs, and parental assistance, making them the riskiest group due to uneven cash flow and dropout risks. Part-time and unemployed borrowers face irregular or temporary income, with social benefits that may lapse or prove insufficient. Self-employed individuals juggle business cycles and personal guarantees, resulting in moderate defaults. The “Other” category likely includes dependents or unusual employment situations backed by third-party guarantees, explaining their lower risk.

### Interest Rate vs Credit Score

![Interest Rate vs Credit Score](interest_vs_credit_score.png)

Lenders use credit scores to calibrate risk-based pricing under Basel III frameworks. Borrowers with scores below 580 pay rates up to 15% to offset higher loss expectations from past delinquencies or limited credit histories. As scores rise into the 650–699 range, rates drop sharply, reflecting improved repayment behavior and lower capital charges. Those above 750 effectively pose no risk, securing rates around 2–3% and incentivizing maintenance of exemplary credit records. The clustering of borrowers around mid-range scores underscores the importance of credit-building strategies in the Austrian market.

### Average Loan Amount by Purpose

![Average Loan Amount by Purpose](loan_amount_by_purpose.png)

Auto financing leads to the largest average loans, driven by high vehicle costs and widespread car ownership in Austria. Depreciation and maintenance costs contribute to the relatively higher default rate. Home improvement loans, backed by real estate collateral and buoyed by government incentives for energy upgrades, sit at a moderate default level. Furniture and appliance financing, while smaller, lacks strong collateral and can spike in default if borrower cash flows are disrupted. Education loans remain the smallest, reflecting subsidies and short repayment horizons, but carry moderate risk when students withdraw or face academic delays. The “Other” purpose category encompasses urgent expenses—such as medical bills—where borrowers prioritize repayment, resulting in the lowest defaults.

[💡 View the Python report](https://github.com/Dan103/Credit-Data-Analysis/blob/dd68f4f1668c9dab9b6f2bccefce564212432eda/Analysis.ipynb)

---

## R Analysis

### Default Rate by Annual Income Band

![Default Rate by Annual Income Band](default_rate_by_annual_income_band.png)

Low-income borrowers typically juggle essential costs without much discretionary income, leading to the highest default rates. Middle-income groups face competing priorities—mortgages, family expenses, and lifestyle maintenance—that can stress budgets under economic pressure. High-income individuals draw on diversified income streams and substantial savings, providing a cushion against unexpected shocks and resulting in the lowest defaults.

### Default Rate by Credit Score Band

![Default Rate by Credit Score Band](default_rate_by_credit_score_band.png)

The dramatic fall in defaults from the Poor to Fair band highlights how even modest improvements in credit behavior significantly lower risk. Achieving a Good score further cuts default probability, facilitating access to cheaper credit and reinforcing positive payment habits. Excellent and Exceptional scores correspond to negligible defaults, reflecting a history of disciplined financial management and strong lender relationships.

### Default Rate by Education Level

![Default Rate by Education Level](default_rate_by_education.png)

Those with only compulsory schooling exhibit slightly higher defaults, likely due to limited access to high-paying roles. Vocational and high-school graduates benefit from Austria’s dual education system, securing steady incomes early on. University graduates have similar or marginally better performance, reflecting professional salaries, but do not markedly outperform vocational peers, showcasing the effectiveness of Austria’s vocational training in fostering financial stability.

### Default Rate by Employment Status

![Default Rate by Employment Status](default_rate_by_employment_status.png)

Students and part-time workers, constrained by sporadic income, face the highest default risks. Unemployed borrowers rely on temporary benefits that may not cover debt obligations long term. Self-employed individuals, while having potential for higher earnings, confront market-driven income swings. Retirees and full-time employees benefit from steady pensions or wages, combined with social protections, resulting in more stable repayment patterns.

### Default Rate by Loan Purpose

![Default Rate by Loan Purpose](default_rate_by_loan_purpose.png)

Car financing sits at the top of the default spectrum due to depreciation and the sizeable principal involved. Education loans are smaller but hinge on student continuation and post-graduation earnings, raising risk if studies are interrupted. Furniture and appliance loans, often for lifestyle upgrades, carry moderate default when households reprioritize spending. Home improvement loans, secured by property value, offer lenders collateral recovery options and enjoy lower default rates. The “Other” category, likely including urgent or medical expenses, shows the lowest defaults as borrowers deem repayment critical.

[💡 View the R report](https://dan103.github.io/Credit-Data-Analysis/Analysis.html)

---

## Conclusions & Recommendations

**Ideal Borrower Profile:**  
- Age 36–55  
- Full-time employed or retired  
- Annual income > €60 k  
- Credit score ≥ 700  
- Financing home improvement  

**High-Risk Borrower Profile:**  
- Under 26 or over 65  
- Student, part-time, or unemployed  
- Annual income < €24 k  
- Credit score < 600  
- Large car or unsecured consumer loan  

**Recommendations:**  
1. **Risk-Based Pricing:** Implement granular interest tiers closely tied to credit score and income, with premium terms for top-tier borrowers.  
2. **Underwriting Enhancements:** Enforce minimum income thresholds, robust employment verification, and require collateral or guarantors for volatile segments.  
3. **Product Design:** Offer fixed-rate, shorter-tenor loans for riskier cohorts, especially amid rising interest rates.  
4. **Early-Warning Monitoring:** Deploy analytic models to flag payment stress among students, part-time workers, and low-income borrowers.  
5. **Financial Education:** Partner with educational institutions and employers to promote credit awareness and budgeting skills.

---

## Appendix

- **Data Sources:** Internal Austrian bank portfolios; KSV/CRIF credit bureau.  
- **Code Repositories:** Python (`Analysis.ipynb`), R (`Analysis.R`).  
- **Supplemental Materials:** Regional performance breakdowns; term-length sensitivity studies; full data dictionary.  
