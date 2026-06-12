# Regression Algorithms Part 2 - Assignment 06

### 1. Multiple Linear Regression & Collinearity

| Term | Definition | Application |
| :--- | :--- | :--- |
| **Multiple Regression** | Predicting a target using multiple input features at once. | Predicting Mobile Phone price using RAM, Storage, and Battery. |
| **Coefficients** | Individual weights assigned to each feature. | A +$10 for every extra 1GB of RAM. |
| **Intercept** | The base prediction when all features are zero. | The base cost of a phone frame/screen. |
| **VIF (Variance Inflation Factor)**| A metric to detect Multicollinearity. | Checking if "Storage in GB" and "Storage in MB" are redundant. |

---

### 2. Scenario Analysis: Multicollinearity

* **What is it?** When two or more input features are highly correlated with *each other*.
* **Why is it bad?** If you try to predict a Phone's Price using "RAM in GB" and "RAM in MB", the math gets confused trying to distribute the importance between the two identical features.
* **The Solution:** Calculate VIF. If a feature has a VIF > 5 or 10, it is redundant and should be dropped to make the model stable.

---

### 3. Multiple Linear Regression Workflow (Mobile Pricing)

```text
┌─────────────────┐
│  Input Features │ ➔ RAM, Storage, Battery Size, Camera Megapixels.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ VIF Check       │ ➔ Identify if any features are redundant and drop them.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Train Algorithm │ ➔ Fit a multidimensional plane through the data points.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Interpret Coefs │ ➔ Determine which feature drives the price up the most.
└─────────────────┘
```

---

### 4. Interpreting Coefficients

* **Example:** If the equation is `Price = (50 * RAM) + (10 * Storage) + 100`:
* **Meaning:** For every 1 GB increase in RAM, the price goes up by $50, assuming Storage stays exactly the same. The intercept ($100) is the base starting price.
