# Credit Risk Default Prediction & Credit History Index (CHI) Framework

> Built an end-to-end credit default prediction and risk segmentation framework using logistic regression, decision trees, ROC optimization, and a custom Credit History Index (CHI) scoring model.

**Author:** Amisha Farhana Shaik  
**Project Type:** Financial Risk Modeling | Credit Scoring | Logistic Regression | Portfolio Risk Strategy  

---

## Business Context

The credit card industry faces significant financial losses due to customer defaults.  

This project analyzes real-world credit data from a Taiwanese bank (2005), contextualized by Taiwan’s 2006 credit card crisis, where aggressive lending led to widespread debt traps and systemic risk.

The objective was to:

- Predict probability of default
- Identify high-risk customers early
- Optimize decision thresholds based on business trade-offs
- Develop a deployable risk segmentation framework

---

## Dataset Overview

- 25 financial & demographic variables
- Monthly repayment status (6 months)
- Bill amounts & payments
- Credit limits
- Education, marital status, age, gender
- Target: Default (binary)

The dataset reflects real repayment behavior during a period of aggressive credit expansion.

---

## Key Exploratory Insights

### Demographics & Default Risk
- Default risk increases with age (peaks ~29% for 60–79 age group)
- Married males show higher default rates (~25.9%)
- Single females show lowest default rates (~19.7%)

### Repayment Behavior
- Severe delays (7 months) consistently show highest default probability
- First-time delays show significantly lower default likelihood
- Short-term delays (2–3 months) sharply increase next-month default probability

### Financial Behavior Patterns
- Average bills increased steadily while payments remained flat
- Many customers paid only minimum amounts despite rising balances
- Lower repayment ratios strongly correlated with default risk

---

## Modeling Approach

### Model 1 – Logistic Regression (All Predictors)
Evaluated using:
- Lift charts
- Decile analysis
- ROC-AUC

Top 20% of customers captured ~50% of defaults.

### Model 2 & 3 – Engineered Repayment Categories
Grouped repayment status into:

- No issue
- First-time delay
- Short-term delay
- Long-term delay
- Severe default

This improved interpretability and predictive signal.

---

## Model Evaluation

- ROC-AUC: 0.7688
- Best operational cutoff: 0.3
- Sensitivity (Recall for defaulters): 48.2%
- Specificity: 89.4%

### Why Sensitivity Was Prioritized

In credit risk:
- False Negatives (missed defaulters) = high financial loss
- False Positives = opportunity cost

Therefore, the model prioritized detecting defaulters early.

Logit Model 3 (cutoff = 0.3) was selected as optimal.

---

## Decision Tree Insights

- 2–3 month short-term delays significantly increase default probability
- First-time delays are manageable if addressed early

**Business Insight:** Early intervention in short-term delays prevents long-term defaults.

---

## Credit History Index (CHI) – Custom Risk Scoring Framework

To make the model operational, I designed a deployable scoring system:

### CHI Score (0–120)

Starting Score: 70 points  
Adjusted by:

**Payment Behavior**
- On-time payment → +3
- 1-month delay → -6
- 2–3 months delay → -12
- 4+ months delay → -24

**Credit Utilization**
- 30–70% → +5
- >70% → -8

**Payment-to-Bill Ratio**
- ≥90% → +6
- <50% → -6

---

## CHI Risk Categories

- High-Risk (CHI < 20)
- Moderate-Risk (20–60)
- Low-Risk (> 60)

### Performance

- High-Risk: ~65% default rate
- Moderate-Risk: ~28%
- Low-Risk: ~12%

Customer Distribution:
- Low-Risk: 53.6%
- Moderate-Risk: 39.1%
- High-Risk: 7.3%

---

## Strategic Implementation Framework

### High-Risk Customers
- Early intervention alerts
- Temporary credit limit reduction
- Structured repayment plans
- Close monitoring

### Moderate-Risk Customers
- Incentives for improved repayment
- Interest rate reductions
- Financial education insights

### Low-Risk Customers
- Credit limit increases
- Loyalty rewards
- Premium product upselling

---

## Business Impact

This framework enables:

- Early identification of potential defaulters
- Reduced bad debt losses
- Targeted intervention strategies
- Risk-adjusted portfolio management
- Improved profitability through segmented customer engagement

---

## Skills Demonstrated

- Logistic Regression & Cutoff Optimization
- ROC-AUC & Lift Analysis
- Feature Engineering for Credit Data
- Risk-Based Model Selection
- Decision Tree Interpretation
- Custom Credit Scoring Model Design
- Financial Risk Strategy Development
- Translating Models into Operational Policy

---

This project demonstrates applications in:

Credit Risk Modeling | Financial Analytics | Portfolio Risk Management | Lending Strategy | Banking Data Science
