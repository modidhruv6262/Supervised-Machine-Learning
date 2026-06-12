# Classification Algorithms Part 1 - Assignment 10

### 1. Algorithm Components & Concepts

| Mathematical Concept | Function / Role | Application in ML |
| :--- | :--- | :--- |
| **Sigmoid Function** | Maps any real value into a range between 0 and 1 | Core activation function for Logistic Regression |
| **Thresholding** | Divides probabilities into distinct classes (e.g., > 0.5) | Converting continuous probability to binary label |
| **Coefficients** | Determines the weight/importance of a feature | Understanding which feature drives the prediction |

---

### 2. Scenario Analysis: Threshold Adjustments

* **1) Instagram Viral Predictor (Default 0.5):** Balanced approach. Predicts viral if it's more likely than not. Good for general analytics.
* **2) High-Stakes Spam Filter (Threshold 0.9):** Requires high confidence to classify as spam. Avoids accidentally blocking legitimate personal emails.
* **3) Medical Disease Screener (Threshold 0.1):** Requires low confidence to trigger a positive flag. Better to over-predict and do further testing than miss a sick patient.

---

### 3. Logistic Regression Workflow (Instagram Example)

```text
┌─────────────────┐
│   Input Data    │ ➔ Features: Likes, Has Caption, etc.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Linear Equation │ ➔ Computes weighted sum of inputs (z = wx + b).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Sigmoid Mapping │ ➔ Converts the linear result into a probability (0 to 1).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Classification  │ ➔ Applies threshold (e.g., 0.5) to output Viral / Not Viral.
└─────────────────┘
```

---

### 4. Key Takeaways: Linear vs Logistic

* **Linear Regression:** Outputs continuous numeric values (e.g., predicting exact number of likes). Can output negative numbers or numbers > 1.
* **Logistic Regression:** Outputs probabilities bounded strictly between 0 and 1 using the Sigmoid curve, making it ideal for categorical yes/no predictions.
