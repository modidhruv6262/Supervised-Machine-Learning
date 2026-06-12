# Regression Algorithms Part 3 - Assignment 08

### 1. Polynomial Regression & Transformations

| Concept | Explanation | Real-World Example |
| :--- | :--- | :--- |
| **Polynomial Regression** | Fitting a curved line instead of a straight line | Epidemic spread over time (exponential curve) |
| **PolynomialFeatures()** | Scikit-learn tool to artificially create curved features (x², x³) | Squaring "Instagram followers" to capture viral effects |
| **Degree** | How many bends the curve is allowed to have | Degree 1 = line, 2 = U-shape, 3 = S-shape |

---

### 2. Scenario Analysis: Linear vs Non-Linear

* **1) Linear Problem:** House price vs Square footage. Usually goes up in a straight steady line. Simple Linear Regression works perfectly.
* **2) Non-Linear Problem:** Plant growth vs Water amount. A little water helps, medium water is perfect (peak growth), too much water drowns the plant (growth drops). This is an upside-down U-shape curve requiring Polynomial Regression.

---

### 3. Polynomial Workflow

```text
┌─────────────────┐
│  Raw 1D Feature │ ➔ Input: [x]
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ PolynomialFeat. │ ➔ Transform into polynomial: [1, x, x², x³]
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Linear Regress. │ ➔ Apply standard Linear Regression to the new 3D features.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Curved Fit    │ ➔ The resulting trendline seamlessly bends to fit the data!
└─────────────────┘
```

---

### 4. The Danger of Overfitting (High Degree)

* **Underfitting (Degree 1):** A straight line trying to fit a U-shaped dataset will completely miss the mark.
* **Good Fit (Degree 2 or 3):** Gently curves to capture the underlying pattern.
* **Overfitting (Degree 15):** The line aggressively zig-zags to hit every single data point perfectly. It memorizes the training noise and will fail spectacularly on new test data.
* **The Fix:** Add L2 Regularization (Ridge) to constrain the polynomial curves from getting too wild.
