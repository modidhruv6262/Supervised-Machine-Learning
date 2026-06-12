# Regularization Techniques - Assignment 09

### 1. Regularization Methods & Behaviors

| Regularization | Penalty Type | Core Behavior | Key Advantage |
| :--- | :--- | :--- | :--- |
| **Lasso Regression** | L1 (Absolute value) | Shrinks some coefficients exactly to zero | Built-in automatic feature selection |
| **Ridge Regression** | L2 (Squared value) | Shrinks all coefficients towards zero but keeps them | Handles highly correlated features well |
| **ElasticNet** | L1 + L2 Mix | Blends both penalties based on `l1_ratio` | Balances feature selection and grouping |

---

### 2. Scenario Analysis: When to use which?

* **1) High-dimensional sparse data (e.g., 10,000 text features):** Lasso Regression is best to zero-out the irrelevant words and keep a simple model.
* **2) Many highly correlated features (e.g., height, weight, BMI):** Ridge Regression is better because it distributes the weights rather than arbitrarily dropping correlated variables.
* **3) Unknown feature importance (e.g., New Zomato dataset):** ElasticNet is the safest choice to let the model optimally tune the balance between L1 and L2.

---

### 3. Feature Selection Workflow (Lasso Example)

```text
┌─────────────────┐
│  Full Dataset   │ ➔ 50+ features loaded into the model.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Apply L1 Penalty│ ➔ Lasso penalizes the absolute size of coefficients.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Coefficient    │ ➔ Weak/Irrelevant feature coefficients become exactly 0.0.
│  Zeroing        │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Feature Subset  │ ➔ Final model only uses the remaining non-zero features.
└─────────────────┘
```

---

### 4. Overfitting & Regularization

* **Unregularized Models:** Can grow huge coefficients trying to fit every single noise point in the training data, leading to massive overfitting.
* **Regularized Models:** By applying an `alpha` penalty, the model is forced to keep its coefficients small and smooth, leading to better generalization on unseen data.
