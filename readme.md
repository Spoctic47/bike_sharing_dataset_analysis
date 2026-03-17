# City Bike Demand Analysis

## Problem Statement

In this assignment, I built end-to-end machine learning pipelines to predict hourly bike rental demand using weather and time-based features.

I approached the problem in two ways:

* **Regression** → Predict the exact number of bike rentals (`count`)
* **Classification** → Predict whether demand is **High** or **Low**

Dataset: *Bike Sharing Demand (Kaggle)*

---

## Approach

The assignment is divided into three main phases:

### 🔹 Phase 1: EDA & Feature Engineering

* Converted datetime into useful features like hour, month, and day of week
* Visualized how demand changes over time and seasons
* Analyzed correlations between weather variables
* Applied PCA to handle redundancy in weather features

### 🔹 Phase 2: Regression

* Models used:

  * Linear Regression
  * Decision Tree Regressor
* Evaluated using:

  * R2 Score
  * RMSE

### 🔹 Phase 3: Classification

* Created a binary target (`high_demand`) using median split
* Models used:

  * Logistic Regression
  * Decision Tree Classifier
* Evaluated using:

  * Accuracy
  * Precision
  * Recall

---

## EDA Insights

* Demand is very low during early morning hours (around 3–5 AM)
* There is a sharp peak around **8-9 AM**, likely due to people commuting to work
* Another even stronger peak appears around **4–6 PM**
* After that, demand gradually drops again

So overall, the pattern is clearly **bimodal**, which strongly reflects daily commuting behavior.

Season-wise, demand is:

* Lowest in spring
* Highest in fall
* Fairly high in summer and winter

---

## PCA Justification

While analyzing the weather variables, I found that `temp` and `atemp` were almost identical (correlation ≈ 0.98). This means they were basically carrying the same information.

To handle thisy, I applied **PCA after standardization**. This helped in:

* Reducing the number of features
* Removing multicollinearity
* Combining weather variables into meaningful components

Which adds stability and increases accuracy.

---

## Model Comparison

### 🔹 Regression

* Linear Regression didn’t perform very well because it assumes a linear relationship.
* Decision Tree performed better and achieved lower RMSE as it was able to capture the non linear relationship.

This makes sense because the demand patterns (like peaks at specific hours) are clearly **nonlinear**

---

### 🔹 Classification

* Logistic Regression gave decent baseline performance.
* Decision Tree performed better, especially in capturing high-demand cases.

Again, this shows that the problem is not linearly separable.

---

## Final Conclusion

Across both regression and classification tasks, **Decision Trees performed better than linear models**.

---
