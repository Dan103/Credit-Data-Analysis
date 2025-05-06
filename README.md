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

The analysis of Austrian consumer-loan data reveals that **age**, **employment**, **credit score**, **income**, and **loan purpose** are key drivers of default risk. Mid-career borrowers (36–55) exhibit the lowest defaults due to stable incomes and established credit histories, while the youngest and oldest cohorts face elevated risk from income volatility and fixed pensions. Full-time employed and retired borrowers default less frequently than students and part-timers, reflecting the availability of consistent cash flow. Credit score remains the most powerful predictor: default rates drop from **8.1 %** (“Poor”) to **0 %** (“Exceptional”), with associated interest spreads reflecting Basel III risk-based pricing and Austrian banks’ conservative risk management. Low-income borrowers (< €24 k) default at **4.4 %** versus **2.4 %** for high earners (> €60 k). Loan purposes backed by collateral (home improvement) carry lower risk than depreciating assets (cars). These insights suggest that lenders should calibrate underwriting and pricing to borrower profiles—favoring high-credit, high-income, stable-income segments and imposing stricter terms for riskier groups.

---

## Introduction & Objective

This report provides a detailed descriptive analysis of Austrian consumer-loan records to identify the demographic, financial, and loan-specific factors that influence default risk. The objectives are to:

1. Uncover which borrower segments exhibit higher or lower default rates.  
2. Interpret these patterns through the lens of Austria’s economic, social, and regulatory environment.  
3. Offer actionable recommendations for Austrian lenders to optimize credit policies, pricing strategies, and risk management.

---

## Data Description

The dataset comprises anonymized consumer-loan records from Austrian lenders, including:  
- **Demographics:** Age group, education level, employment status.  
- **Financials:** Annual income band, credit score band, interest rate, loan amount.  
- **Loan Details:** Purpose category (Car, Education, Furniture/Appliances, Home improvement, Other).  
- **Outcome:** Binary indicator of default within 12 months.  

Data aggregation by category preserves confidentiality while enabling robust subgroup analysis.

---

## Methodology

- **Tools:**  
  - **Python** (pandas, Matplotlib, Seaborn) for exploratory analysis and interactive charts.  
  - **R** (tidyverse, ggplot2) for detailed default-rate breakdowns and layered visualizations.  
- **Process:**  
  1. Calculate default rates per categorical band.  
  2. Generate visualizations to identify trends and correlations.  
  3. Contextualize findings within Austria’s socio-economic and regulatory framework.  
- **Scope:** Descriptive analytics only; no predictive modeling. Emphasis on clarity and actionable insights.

---

## Python Analysis

### Default Rate by Age Group

![Default Rate by Age Group](images/default_rate_by_age_group.png)

#### Analysis  
The U-shaped default curve suggests two primary risk drivers: **income volatility** among the young and **fixed-income constraints** among the elderly. Borrowers aged 18–25 lack steady employment and often carry educational debt, which, combined with entry-level wages, increases delinquency. Conversely, the 66–75 cohort relies heavily on pensions that may not keep pace with living costs or healthcare expenses, leading to strained budgets and higher default.

#### Austrian Context  
Austria’s NEET rate for 18–24 year-olds is around 12 %, indicating significant exposure among student borrowers who may juggle part-time work and studies. Meanwhile, pensioners receive a median pension of roughly €25.8 k, which can be eroded by rising healthcare and energy costs—a dynamic exacerbated by recent inflation.

#### Sub-conclusion  
Borrowers aged **36–55** are the safest segment, benefiting from peak earning years and low unemployment; extra caution is warranted for applicants under 26 or over 65.

---

### Employment Status Distribution

![Employment Status Distribution](images/employment_status_pie.png)

#### Analysis  
Full-time employed borrowers (55 %) default at **~3.2 %**, reflecting stable salaries and employer benefits. Students (5.1 % of the portfolio) default at **5.2 %**, driven by limited income and irregular payment capacity. Part-time workers and the unemployed show elevated defaults (~4 %), underscoring the risk of precarious or benefit-dependent incomes. Self-employed borrowers, while entrepreneurial, face cyclical business risks and thus default at **3.4 %**.

#### Austrian Context  
Generous unemployment benefits and a robust pension system cushion income shocks, but transitions (e.g., from unemployment to work) can create payment gaps. Austria’s vocational training system produces a stable self-employed segment, yet small business owners remain vulnerable to macroeconomic swings.

#### Sub-conclusion  
Standard full-time employees and retirees represent low-risk groups; enhanced documentation and co-signer requirements should apply for students, part-timers, and unemployed borrowers.

---

### Interest Rate vs Credit Score

![Interest Rate vs Credit Score](images/interest_vs_credit_score.png)

#### Analysis  
The pronounced negative correlation confirms that Austrian lenders employ **risk-based pricing**: borrowers with scores below 580 pay rates up to 15 % to offset higher expected losses, whereas those above 750 secure rates as low as 2 %. The steep drop in default—8.1 % for “Poor” to 0 % for “Exceptional”—validates Basel III capital allocation models and regulatory incentives for low-risk lending.

#### Austrian Context  
Austria’s centralized credit bureaus (KSV/CRIF) provide comprehensive repayment histories, enabling granular score analytics. Regulatory caps on usury ensure interest spreads remain within EU guidelines, but banks still differentiate via score bands to manage risk and capital costs.

#### Sub-conclusion  
Credit score is the **primary lever** for both pricing and credit approval; automated workflows should fast-track Exceptional and Very Good scores while imposing manual review or higher collateral on Poor and Fair applicants.

---

### Average Loan Amount by Purpose

![Average Loan Amount by Purpose](images/loan_amount_by_purpose.png)

#### Analysis  
Car loans average €21 k—reflecting high vehicle ownership but also increasing exposure to depreciation. Home-improvement loans (€15 k) benefit from rising property values and collateral security, reducing loss severity despite mid-range principal. Education loans (€7 k) are smaller and combine public subsidies, leading to moderate default (3.4 %). Furniture/appliance financing (€9 k) and “Other” (€11 k) fill consumer demand but face less predictable resale value.

#### Austrian Context  
With a homeownership rate of 54.5 %, many borrowers leverage property equity for home projects at favorable rates or via subsidized energy-efficiency loans. Automotive financing growth correlates with urban-rural transport needs but introduces volatility as vehicles depreciate and maintenance costs rise.

#### Sub-conclusion  
Loan size and collateral quality vary by purpose: home-secured loans warrant larger amounts at lower rates, whereas auto and unsecured consumer loans require tighter limits and stronger underwriting.

[💡 View the Python report](https://github.com/Dan103/Credit-Data-Analysis/blob/dd68f4f1668c9dab9b6f2bccefce564212432eda/Analysis.ipynb)

---

## R Analysis

### Default Rate by Annual Income Band

![Default Rate by Annual Income Band](images/default_rate_by_annual_income_band.png)

#### Analysis  
A clear inverse relationship shows default falling from **4.4 %** (0–24 k) to **2.4 %** (60 k+). Low-income borrowers often have limited savings buffers and may prioritize essential expenses over debt service. The middle band (24–60 k) experiences transitional financial stress—covering mortgages, family costs, and consumer credit.

#### Austrian Context  
Austria’s progressive tax regime and social transfers mitigate some income volatility, yet disposable income below €24 k remains tight, especially for single-income households or part-time workers. High-earning professionals benefit from diversified investments and dual-income families.

#### Sub-conclusion  
Income band is a **critical underwriting filter**: minimum income thresholds and scalable credit limits aligned to earnings can materially reduce default risk.

---

### Default Rate by Credit Score Band

![Default Rate by Credit Score Band](images/default_rate_by_credit_score_band.png)

#### Analysis  
The default rate plunges from **8.1 %** (Poor) to **4.7 %** (Fair), then halves again to **2.0 %** (Good), culminating in **0 %** at Exceptional. This gradient underscores the non-linear impact of creditworthiness: small improvements in score yield outsized reductions in default probability.

#### Austrian Context  
Robust reporting requirements for loans above €75 k enrich credit files, while even smaller loans feed data into bureaus. Banks leverage these insights to automate approvals, reducing operational costs and focusing manual underwriting on borderline cases.

#### Sub-conclusion  
Credit score bands should map directly to credit policy tiers—automated approval for Good+, enhanced monitoring for Fair, and possibly denial or secured lending for Poor.

---

### Default Rate by Education Level

![Default Rate by Education Level](images/default_rate_by_education.png)

#### Analysis  
Default rates are narrowly clustered: **3.3 %–3.5 %**, with the least-educated slipping marginally higher. The minimal variance suggests that educational attainment per se is less predictive than income or credit score, though it may indirectly influence employability and earning potential.

#### Austrian Context  
Austria’s dual education system (60 % in vocational tracks) delivers high employment outcomes across education levels. Lifelong learning programs and adult education inflate overall attainment, compressing default differences.

#### Sub-conclusion  
Education level offers **limited standalone value** for risk assessment in Austria; focus should remain on direct financial indicators.

---

### Default Rate by Employment Status

![Default Rate by Employment Status](images/default_rate_by_employment_status.png)

#### Analysis  
Students default at **5.2 %**, the highest of any group, followed by part-time (4.0 %) and unemployed (3.9 %). Full-time employed and retirees converge at **3.2 %**, reflecting consistent income streams. Self-employed (3.4 %) face more volatility than salaried workers but less than those with intermittent income.

#### Austrian Context  
Generous unemployment benefits create a temporary cushion, but benefit exhaustion can precipitate defaults. Pensioners enjoy stable but limited cash flows, and high mandatory social contributions ensure income predictability for salaried workers.

#### Sub-conclusion  
Employment status is a **key risk dimension**—rigorous income verification, benefit documentation, and contingency planning are essential for non-standard workers.

---

### Default Rate by Loan Purpose

![Default Rate by Loan Purpose](images/default_rate_by_loan_purpose.png)

#### Analysis  
Car loans default at **3.9 %**, the highest, due to depreciation and larger average balances. Home-improvement loans default at **3.2 %**, buoyed by property equity. “Other” purposes (2.7 %) likely include emergency or short-tenor loans with immediate need and rapid payoff.

#### Austrian Context  
Austrian real estate markets have shown steady appreciation, reducing loss-given-default on mortgages and improvements. Automotive financing must account for resale value declines and maintenance cost variability, which amplify default risk.

#### Sub-conclusion  
Loan purpose should drive tailored underwriting: favor collateralized home loans, impose stricter down-payments or co-signers for auto and unsecured loans.

[💡 View the R report](https://dan103.github.io/Credit-Data-Analysis/Analysis.html)

---

## Conclusions & Recommendations

- **Synthesis:**  
  - **Demographics:** Ages 36–55, full-time employed or retired, with incomes > €24 k and credit scores ≥ 700, exhibit the lowest default rates.  
  - **Financial Metrics:** Credit score and income are the strongest predictors of default; loan purpose and collateral quality further refine risk.  

- **Strategic Recommendations:**  
  - **Risk-Based Pricing:** Implement tiered interest rate bands tightly aligned to credit score and income.  
  - **Underwriting Controls:** Require minimum income of €24 k, stable employment verification, and higher collateral or co-signers for high-risk segments.  
  - **Product Design:** Offer fixed-rate, shorter-term loan products to borrowers vulnerable to interest rate fluctuations.  
  - **Monitoring & Education:** Deploy early-warning systems for at-risk groups (students, part-timers) and provide targeted financial literacy programs.  

- **Ideal Borrower Profile:**  
  - Age 36–55, full-time employed, income > €60 k, credit score ≥ 700, financing home improvement.  

- **Worst Borrower Profile:**  
  - Age < 26 or > 65, student/part-time/unemployed, income < €24 k, credit score < 600, large car loan.  

---

## Appendix

- **Data Sources:** Internal Austrian bank portfolios, KSV/CRIF credit bureau.  
- **Repositories:**  
  - Python notebook: `Analysis.ipynb`  
  - R scripts: `Analysis.R`  
- **Supplemental Materials:** Regional breakdowns, term-length analyses, full data dictionary.
