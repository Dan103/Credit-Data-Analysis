# Credit-Data-Analysis
Python + R


[💡 View the Python report](https://github.com/Dan103/Credit-Data-Analysis/blob/dd68f4f1668c9dab9b6f2bccefce564212432eda/Analysis.ipynb)
[💡 View the R report](https://dan103.github.io/Credit-Data-Analysis/Analysis.html)



# 🏦 Credit‑Risk Defaults — A Python + R Story

A 360° walkthrough of 5 000 consumer‑loan records.  
Python powers the data pipeline; R refines the visuals and statistical cross‑checks.

| 📔 Read the full Python notebook | **[`analysis.ipynb`](<link‑to‑ipynb>)** |
| 📑 Dive into the styled R report | **[`analysis.html`](<link‑to‑html>)** |

---

## 1. Average Loan Amount by Purpose

![Avg Loan Amount](images/loan_amount_by_purpose.png)

### What we see  
Car loans dominate at **\$20 k**—double any other purpose. Home‑improvement follows at \$15 k; furniture, “Other,” and education taper down to \$6–11 k.

### Why it matters  
* **Ticket‑size concentration risk**: a single purpose (car) holds a fifth of portfolio exposure.  
* Larger balances amplify both credit risk and LGD (loss‑given‑default).

### Why it’s happening  
1. **Depreciating collateral**: auto dealers push financing with minimal down‑payments.  
2. **Marketing bias**: the bank’s branch network heavily advertises car finance promotions.

### Business moves  
* Introduce **purpose‑based pricing**: +60 bps surcharge on car loans covers incremental capital.  
* Pilot a **co‑ownership lien** program—transfer some LGD to dealers.

---

## 2. Interest Rate vs Credit Score

![Interest vs Score](images/interest_vs_credit_score.png)

### What we see  
Five dense “bricks” appear—each credit‑score band clusters around a distinct rate range.  
* **Poor (≤ 580)**: 12–15 %  
* **Fair**: 8–12 %  
* **Good**: 5–8 %  
* **Very Good**: 3–5 %  
* **Exceptional (≥ 800)**: 2–4 %

### Why it matters  
A perfectly monotonic pricing ladder signals underwriting discipline—score bands translate to APR bands.

### Why it’s happening  
* The pricing engine uses discrete band adjustments, not a continuous curve.  
* Lenders overlay **manual exceptions** (e.g., loyalty discounts) only within bands, preserving the staircase.

### Business moves  
* Consider a **micro‑band** approach (e.g., 20‑point slices) to capture granular risk and harvest extra spread.  
* Feed the scatter into a **price‑elasticity model**—map conversion vs. rate at each score.

---

## 3. Employment Status Distribution

![Employment Pie](images/employment_status_pie.png)

### What we see  
Full‑time employees drive **55 %** of originations. Retirees (13.7 %) and part‑timers (9.3 %) offer secondary volume; students, unemployed, and “other” form the tail.

### Why it matters  
Portfolio health leans heavily on the macro labour market—any shock to full‑time employment threatens over half the book.

### Why it’s happening  
* Employer‑payroll integrations speed up income verification, nudging employees through the funnel.  
* Retirees are attracted by fixed‑rate promos and pension‑proof income screens.

### Business moves  
* Launch a **dynamic LTI cap** linked to local unemployment indices—tighten DTI for regions showing layoffs.  
* Diversify volume into gig‑economy cohorts with alternative data (e.g., platform payout histories).

---

## 4. Default Rate by Age Group

![Default Age](images/default_rate_by_age_group.png)

| Age Band | Default Rate | Odds vs. Portfolio |
|----------|--------------|--------------------|
| 18–25 | **4.3 %** | 1.4 × |
| 26–35 | 3.1 % | 1.0 × |
| 36–45 | 3.7 % | 1.2 × |
| 46–55 | 3.1 % | 1.0 × |
| 56–65 | **2.7 %** | 0.9 × |
| 66–75 | **4.9 %** | 1.6 × |

### What we see  
A U‑curve: risk elevated at the youngest and oldest ends, with a plateau in mid‑career.

### Why it’s happening  
* **Young borrowers** lack credit history and exhibit income volatility.  
* **Older borrowers** face retirement income transitions and health expenses.  
* Mid‑career (26‑55) enjoy peak earnings and credit tenure.

### Business moves  
* Introduce **age × purpose** policy caps (e.g., restrict 7‑year car loans to ≤ 60 yrs).  
* Offer **payment‑holiday insurance** targeted at 18‑30 yr cohort to mitigate shocks.

---

## 5. Default Rate by Credit Score Band

![Default Score](images/default_rate_by_credit_score_band.png)

### What we see  
Risk halves with each band up‑step—from **8.1 %** (Poor) to **0 %** (Exceptional).

### Why it’s happening  
* Score algorithm already embeds utilisation, delinquencies, and depth of credit.  
* Exceptional band enjoys self‑selection: only 4 % of applicants qualify.

### Business moves  
* **Auto‑decline** Poor scores unless mitigants (collateral, co‑signer) exist.  
* Push **pre‑approved offers** to Very‑Good/Exceptional leads—ultra‑low PD supports higher cross‑sell limits.

---

## 6. Default Rate by Annual Income Band

![Default Income](images/default_rate_by_annual_income_band.png)

### What we see  
> Income ↑ → Default ↓

* \(0–24 k\): **4.4 %**  
* \(24–60 k\): **3.2 %**  
* \(60 k+\): **2.4 %**

### Why it’s happening  
Higher income dampens DTI and cushions emergency liquidity needs.

### Business moves  
* Embed **income elasticity** in pricing: –20 bps for every \$20 k above \$60 k ceiling.  
* Spice acquisition strategy with **soft‑pull pre‑screening** on payroll data.

---

## 7. Default Rate by Loan Purpose

![Default Purpose](images/default_rate_by_loan_purpose.png)

| Purpose | Default % |
|---------|-----------|
| Car | **3.9** |
| Education | 3.4 |
| Furniture / Appliances | 3.4 |
| Home improvement | 3.2 |
| Other | 2.7 |

### What we see  
Car loans command the highest risk again, mirroring ticket size. “Other” sits safest—often small, short‑term cash needs.

### Business moves  
* **Dealer partnership pricing**: shift partial credit risk back to vendors via recourse clauses.  
* Offer **secured home‑improvement lines** to swap from unsecured instalments to collateralised products.

---

## 8. Default Rate by Employment Status

![Default Employment](images/default_rate_by_employment_status.png)

| Status | Default % |
|--------|-----------|
| Student | **5.2** |
| Part‑time | 4.0 |
| Unemployed | 3.9 |
| Self‑employed | 3.4 |
| Retired | 3.2 |
| Employed | 3.2 |
| Other | 2.6 |

### Interpretation  
* Full‑time employment halves risk vs. students.  
* Part‑timers exceed unemployed risk—suggests under‑hours precarity.

### Business moves  
* Require **co‑borrower** on student loans above \$5 k.  
* Complement employment status with **tenure length**: seasoned self‑employed (> 3 yrs) often out‑perform W‑2s.

---

## 9. Default Rate by Education

![Default Education](images/default_rate_by_education.png)

### Finding  
Higher education trims about **20 bps** risk per tier.

### Why  
* Education ⇒ higher lifetime earnings, **even before** current salary feeds into the model.  
* Better financial literacy reduces delinquency incidents.

### Action  
Add education level to segmentation marketing—university‑educated prospects warrant larger credit‑line offers.

---

## Conclusion & Next Steps

The cross‑tool approach (Python for heavy data prep, R for polished visuals) surfaces **three actionable levers**:

1. **Purpose‑size‑price triad**: Car loans need risk‑adjusted pricing and dealer recourse.  
2. **Demographic overlays**: Age and employment status interact strongly—custom scorecards by life stage will outperform a one‑size‑fits‑all model.  
3. **Micro segmentation** by income and credit‑score micro‑bands unlocks incremental NIM without inflating risk.
