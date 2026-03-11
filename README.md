SBA Loan Default Prediction using Logistic Regression
📌 Project Overview

This project builds a Logistic Regression model to predict the probability of loan default using the SBA (Small Business Administration) case dataset.

The objective is to:

Reproduce published model coefficients (Table 7 & 8)

Evaluate classification performance on validation data

Analyze gains and lift

Perform cost-sensitive threshold selection

Provide business interpretation of model outputs

🧠 Business Problem

Banks must decide whether to approve or deny a loan application.

Two types of mistakes exist:

Approving a risky loan (high financial loss)

Denying a safe loan (lost interest income)

This project explores how different decision thresholds impact business risk and profitability.

🛠 Technologies Used

Python

Pandas

NumPy

Scikit-learn

Statsmodels

Matplotlib

dmba (for gains & lift charts)

📊 Model Details

Reduced Logistic Regression Model (Table 8 predictors):

RealEstate

Portion

Recession

Model coefficients reproduced to 4 decimal places using:

sklearn LogisticRegression (liblinear)

sklearn LogisticRegression (lbfgs)

📈 Model Evaluation

Validation Set Results (cutoff = 0.50):

Accuracy: 0.6784

Recall (Sensitivity): 0.0873

Specificity: 0.9799

Precision: 0.6889

F1-score: 0.1550

Key Insight:

The model is strong at identifying safe loans but weak at catching defaults at the 0.5 cutoff.

💰 Cost-Sensitive Decision Analysis

Instead of using the default 0.50 cutoff, we compute business-driven thresholds.

Example:

For a $1,000,000 loan at 10% interest:

Cost-based cutoff:

p* = 100,000 / (100,000 + 1,000,000) = 0.0909

This shows why business costs must influence classification decisions.

📉 Gains & Lift

First decile lift: 1.6056

Interpretation:

The top 10% of loans flagged by the model contain 1.61x more defaults than random selection.

📂 Files
SBA_Final.ipynb → Complete modeling and evaluation notebook

🚀 How to Run

Install dependencies: pip install pandas numpy scikit-learn statsmodels matplotlib dmba
Place SBAcase.11.13.17.csv in the same directory

Run the notebook in Jupyter

📌 Key Takeaways

Logistic regression can effectively rank loan risk

Decision threshold must reflect financial cost structure

Default 0.50 cutoff is rarely optimal in lending decisions

Precision–recall tradeoff is critical in credit risk modeling
