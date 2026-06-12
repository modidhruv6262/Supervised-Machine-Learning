# Regression Model Evaluation - Assignment 07

### 1. Regression Evaluation Metrics

| Metric | Full Form | Interpretation | Ideal Value |
| :--- | :--- | :--- | :--- |
| **MAE** | Mean Absolute Error | Average error in the same units as the target. Easy to understand. | 0 (Lower is better) |
| **MSE** | Mean Squared Error | Average of squared errors. Heavily punishes large outlier errors. | 0 (Lower is better) |
| **RMSE** | Root Mean Squared Error | Square root of MSE. Punishes large errors but remains in target units. | 0 (Lower is better) |
| **R² Score** | Coefficient of Determination | Percentage of variance explained by the model. | 1.0 (Higher is better) |

---

### 2. Scenario Analysis: Picking the Right Metric

* **1) Swiggy Delivery Prediction:** If you want to know "on average, how many minutes off is our ETA?", **MAE** is the best choice because it gives a straightforward "± 5 minutes" answer.
* **2) Medical Dosage Prediction:** If a small error is okay but a massive error is fatal, you should use **MSE or RMSE**, because they exponentially punish large mistakes.
* **3) Comparing Models:** If you want to pitch your model to a manager and say "my model explains 85% of why prices change", use the **R² Score**.

---

### 3. Residual Plots Explained

* **What is a Residual?** The difference between the actual value and the predicted value (Error).
* **What is a Residual Plot?** A scatter plot showing predictions on the X-axis and their residuals on the Y-axis.
* **How to read it:**
    * **Good:** A random cloud of dots tightly clustered around the zero line. (Model captured the pattern).
    * **Bad:** A U-shape, funnel shape, or clear curve. (The model missed a non-linear pattern or variance is unstable).

---

### 4. Evaluating Model Performance (Example)

```text
┌─────────────────┐
│     Model A     │ ➔ RMSE: 8 mins, R²: 0.65
└─────────────────┘
         │
         ▼
┌─────────────────┐
│     Model B     │ ➔ RMSE: 5 mins, R²: 0.88
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Conclusion    │ ➔ Model B is vastly superior. It has less error and explains more variance.
└─────────────────┘
```
