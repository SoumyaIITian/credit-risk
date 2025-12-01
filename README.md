# Credit Risk Probability of Default (PD) Model

## Overview

This repository contains a **Basel-compliant Probability of Default (PD) model** developed using the "Give Me Some Credit" dataset. The model predicts the likelihood of a borrower experiencing serious delinquency (90+ days past due) within 2 years.

## Methodology

The project follows the standard banking risk modeling framework:

1. **Data Sanitization:** Imputed missing `MonthlyIncome` (Median) and `NumberOfDependents` (Mode).

2. **Feature Engineering:**

   * **Binning:** Quantile-based binning to handle outliers.

   * **Weight of Evidence (WoE):** Transformed continuous variables into monotonic risk factors.

   * **Information Value (IV):** Selected features with `IV > 0.02` (Age, Utilization, DebtRatio, Income).

3. **Modeling:**

   * **Logistic Regression:** Chosen for regulatory transparency and interpretability.

   * **Performance:** Achieved **AUC = 0.794**.

4. **Scorecard Calibration:**

   * Scaled model probabilities to a standard credit score range (300-850).

   * **Parameters:** Base Score = 600, PDO = 20, Odds = 50:1.

## Results

* **Key Driver:** `RevolvingUtilizationOfUnsecuredLines` was the strongest predictor (IV ~ 1.11).

* **Coefficient Analysis:** All WoE coefficients are negative, confirming that higher WoE (Good Behavior) correlates with lower Default Probability.

## Tech Stack

* **Python:** Pandas, NumPy, Scikit-learn

* **Visualization:** Matplotlib, Seaborn
