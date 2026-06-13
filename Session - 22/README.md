# Case Study - Session 22

### 1. The Capstone Dataset: Zomato

| Concept | Explanation | Real World Implication |
| :--- | :--- | :--- |
| **Data Cleaning** | Real data is messy. Text in numeric columns, NaN values, and crazy outliers are the norm. | The Zomato dataset has strings mixed in. If you don't use `pd.to_numeric` aggressively, your model will crash. |
| **Data Leakage** | Accidentally including the target variable (or a derivative of it) in your features. | If we use `scaled_rating` to predict if the restaurant has a `>4.0 rating`, the model cheats and gets 100% accuracy. We must exclude it from `X`. |
| **Encoding** | Converting text categories (like "Chinese") into numbers (like `2`) because computers only speak Math. | LabelEncoder assigns unique integers. Without it, Random Forest cannot process locations like "Koramangala". |

---

### 2. Scenario Analysis: Handling Imbalanced Reviews

* **The Problem (Imbalanced Data):** Most restaurants on Zomato cluster around a `3.5` rating. Very few have `> 4.0`. If a model always guesses "No, it's not a 4.0+", it will have a massive 90% accuracy but be completely useless!
* **The Fix (SMOTE):** SMOTE stands for **Synthetic Minority Over-sampling Technique**. It physically hallucinates *new*, fake high-rated restaurants based on the math of the real ones, forcing a 50/50 balance.
* **The Result:** The model is finally forced to learn *why* a restaurant gets > 4.0, rather than just being lazy.

---

### 3. Algorithm Workflow (End-to-End Pipeline)

```text
┌─────────────────┐
│ Raw Data Load   │ ➔ Extract Zomato CSV. Read head/info/describe.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Preprocessing   │ ➔ Force strings to NaN. Drop NaNs. Remove IQR Outliers.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Feature Engine  │ ➔ LabelEncode categories. StandardScaler for prices. Target creation (>4.0).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Balancing       │ ➔ Apply SMOTE to the training set only (never the test set!).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Model Tuning    │ ➔ GridSearchCV on Random Forest to dial in max_depth and n_estimators. Evaluate via ROC-AUC.
└─────────────────┘
```

---

### 4. Key Takeaways

* **ROC-AUC is King:** When dealing with imbalanced classes, Accuracy is a lie. ROC-AUC looks at the model's ability to rank probabilities correctly, making it the supreme metric.
* **GridSearchCV:** Blindly picking parameters is a waste of time. GridSearchCV brutally tests every single combination of parameters to find the mathematical peak of the algorithm's performance.
* **We Made It:** From basic math to an end-to-end Machine Learning pipeline utilizing real world messy data, Synthetic Over-sampling, and Hyperparameter tuning!
