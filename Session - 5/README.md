# Regression Algorithms Part 1 - Assignment 05

### 1. Simple Linear Regression Concepts

| Concept | Description |
| :--- | :--- |
| **Simple Linear Regression** | Drawing a single straight line through data points to minimize overall error. |
| **Independent Variable (X)** | The input feature you control or observe (e.g., Instagram usage hours). |
| **Dependent Variable (y)** | The target outcome you want to predict (e.g., Remaining Battery %). |
| **MSE (Mean Squared Error)** | The average of the squared differences between predicted and actual values. |

---

### 2. Scenario Analysis: Simple Linear Regression

* **1) Screen Time vs. Battery:** As screen time goes up, battery goes down. This is a negative linear relationship.
* **2) Study Hours vs. Test Score:** As study hours go up, test scores generally go up. This is a positive linear relationship.
* **3) Shoe Size vs. Intelligence:** No correlation. A linear regression line here would just be flat and useless.

---

### 3. Simple Linear Regression Workflow

```text
┌─────────────────┐
│   Collect Data  │ ➔ Hours spent on Instagram vs Battery % at end of day.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Plot Scatterplot│ ➔ Visualize the dots on an X/Y graph to see the trend.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Train Algorithm │ ➔ Model calculates the best slope (m) and intercept (c).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Draw Trendline  │ ➔ Plot the predicted line (y = mx + c) over the dots.
└─────────────────┘
```

---

### 4. Understanding MSE

* **Why Square the Errors?** If a prediction is off by +5% and another by -5%, just adding them gives 0 error (which is wrong). Squaring them makes both positive (25 + 25 = 50). It also heavily penalizes very large errors.
* **Goal:** A perfect model has an MSE of 0. We train our model to find the line that results in the lowest possible MSE.
