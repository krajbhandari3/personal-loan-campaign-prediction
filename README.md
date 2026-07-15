# Personal Loan Campaign Purchase Prediction

## Business Problem
A bank wants to identify which customers are most likely to purchase a 
personal loan, so marketing campaigns can be targeted more efficiently 
instead of contacting the full customer base.

## Approach
- Analyzed 5,000 customer records across 14 features (income, family size, 
  education, spending, account holdings, etc.)
- Cleaned data: corrected negative values in Experience, addressed 
  right-skewed Mortgage data, fixed categorical columns stored as integers, 
  dropped non-predictive ID column
- Conducted EDA to understand which customer attributes relate to loan 
  purchase behavior
- Built a baseline Decision Tree model, then applied pre-pruning to 
  reduce overfitting and improve generalization

## Key Findings
- **Income is the single strongest predictor** of loan purchase — the 
  decision tree's root split is on income (≤$116.5K threshold)
- For high-income customers, **family size and education level** further 
  separate likely loan-takers
- For lower-income customers, **spending (CCAvg)** and **CD Account 
  ownership** become the key differentiators — CD_Account is a powerful 
  signal within the $92.5K–$116.5K income band specifically
- Pre-pruning improved **test precision from 92.7% to 98.5%**, cutting 
  false positives from 11 down to 2 — meaning marketing calls are far 
  more efficiently targeted
- The pruned model showed a much smaller train/test performance gap, 
  confirming reduced overfitting and better generalization to new customers
- This involved a real precision/recall trade-off: slightly lower recall 
  in exchange for substantially higher precision and a more reliable model

## Business Recommendations
- **Prioritize high-income segments first:** Income is the dominant driver 
  — campaigns should be weighted toward customers above the $116.5K threshold
- **Use family size and education to refine high-income targeting:** Within 
  the high-income segment, larger families and higher education levels 
  further indicate loan interest
- **Don't ignore mid-income customers with CD accounts:** This segment 
  shows a distinct, exploitable pattern worth a separate targeted campaign
- **Favor precision over recall for this use case:** Given the cost of 
  outreach, the pruned model's higher precision (fewer wasted calls) is 
  the better business trade-off than casting a wider net

## Model Performance
- Model: Decision Tree Classifier (baseline vs. pre-pruned comparison)
- Test Precision improved from 92.7% to 98.5% after pruning
- False positives reduced from 11 to 2
- Train/test performance gap narrowed substantially post-pruning, 
  confirming better generalization

## Tools Used
Python, Pandas, NumPy, Scikit-learn, Matplotlib/Seaborn

## Background
Completed as part of the Post Graduate Program in AI & Machine Learning 
(UT Austin McCombs School of Business). Second project in a portfolio 
transitioning from Power BI/Business Intelligence into applied ML and 
Analytics Engineering.
