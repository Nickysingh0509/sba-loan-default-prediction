# 📊 SBA Loan Default Prediction  
### Logistic Regression for Credit Risk Modeling

> A cost-sensitive machine learning project focused on predicting small business loan default risk and optimizing decision thresholds for real-world banking applications.

---

## 🔎 Project Overview

This project builds and evaluates a Logistic Regression model to predict the probability of default for SBA (Small Business Administration) loans.

Rather than stopping at model accuracy, this analysis goes further by:

- Reproducing published model coefficients from academic research
- Evaluating classification performance using multiple metrics
- Analyzing gains and lift for ranking performance
- Implementing cost-based threshold optimization
- Demonstrating how business costs should influence lending decisions

The focus is not just prediction — but **risk management and profitability trade-offs**.

---

## 🏦 Business Context

Banks face two types of costly mistakes:

- **False Negative (Approve a risky loan)** → Potential loss of entire principal  
- **False Positive (Deny a safe loan)** → Lost interest income  

Using a default 0.50 cutoff probability is often unrealistic in lending.

This project demonstrates how to determine optimal decision thresholds based on:

- Financial loss asymmetry
- Misclassification costs
- Precision–recall trade-offs
- Business risk tolerance

---

## 🧠 Model Specification

Final Reduced Logistic Regression Model (Table 8 replication):

**Predictors:**
- `RealEstate`
- `Portion`
- `Recession`

**Estimated Coefficients (replicated to 4 decimals):**

| Variable      | Estimate |
|---------------|----------|
| Intercept     | 1.3931   |
| RealEstate    | -2.1282  |
| Portion       | -2.9875  |
| Recession     | 0.5041   |

Model fitted using:
- `sklearn.LogisticRegression (liblinear)`
- `sklearn.LogisticRegression (lbfgs)`
- Regularization neutralized (C = 1e10)

---

## 📈 Model Performance (Validation Set)

Using 0.50 cutoff:

| Metric        | Value   |
|---------------|---------|
| Accuracy      | 0.6784  |
| Recall        | 0.0873  |
| Specificity   | 0.9799  |
| Precision     | 0.6889  |
| F1-score      | 0.1550  |

### Insight

The model is highly specific (good at identifying safe loans)  
but performs poorly at catching defaults under the 0.50 threshold.

This highlights why threshold tuning is essential in credit risk modeling.

---

## 📊 Gains & Lift Analysis

- First Decile Lift: **1.61**

Interpretation:

The top 10% of loans ranked by predicted probability contain  
**1.61 times more defaults than random selection**.

This confirms that the model effectively ranks high-risk loans toward the top.

---

## 💰 Cost-Sensitive Threshold Optimization

### Scenario:  
Loan Amount = $1,000,000  
Interest Rate = 10%  

- Cost of False Positive = $100,000  
- Cost of False Negative = $1,000,000  

Cost-based optimal cutoff:
