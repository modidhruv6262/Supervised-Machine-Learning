# Data Processing Part 1 - Assignment 03

### 1. Data Cleaning & Preprocessing Techniques

| Data Issue / Feature | Preprocessing Technique | Scikit-learn Tool |
| :--- | :--- | :--- |
| **Missing Numeric Values (Age)** | Median Imputation | `SimpleImputer(strategy='median')` |
| **Missing Categorical (Team)** | Mode Imputation | `SimpleImputer(strategy='most_frequent')` |
| **Categorical Non-Ordinal (Venue)** | One-Hot Encoding | `OneHotEncoder` |
| **Categorical Ordinal/Target (Role)** | Label Encoding | `LabelEncoder` |

---

### 2. Scenario Analysis: Imputation Strategies

* **1) Mean vs Median:** If predicting player age and one player's data is recorded as 999 by mistake, the **mean** will be heavily skewed. The **median** is robust against such extreme outliers.
* **2) Most Frequent (Mode):** When dealing with text categories like IPL Teams, calculating an average makes no sense. We substitute the missing team with the most commonly occurring team.

---

### 3. Data Processing Workflow (IPL Example)

```text
┌─────────────────┐
│   Raw IPL Data  │ ➔ Dataset contains missing ages, empty teams, and raw text.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Missing Values  │ ➔ Fill Age with Median. Fill Team with Mode.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Feature Scaling │ ➔ Ensures numerical columns are ready for distance metrics.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Categorical Enc │ ➔ Convert Venues to 1s/0s (One-Hot) and Roles to ints (Label).
└─────────────────┘
```

---

### 4. Encoding: One-Hot vs Label

* **Label Encoding:** Assigns integers (0, 1, 2). Should only be used for targets (`y`) or ordinal data (e.g., Low, Medium, High). If used on IPL venues, the model might mathematically assume Venue 2 is "greater" than Venue 1.
* **One-Hot Encoding:** Creates separate columns for each category (e.g., `is_Mumbai`, `is_Delhi`) with 1 or 0. This prevents the model from assuming false mathematical hierarchies among cities.
