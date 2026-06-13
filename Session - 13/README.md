# Classification Algorithms Part 4 - Session 13

### 1. Random Forest Concepts

| Concept | Explanation | Real-World Benefit |
| :--- | :--- | :--- |
| **Random Forest** | An ensemble model that trains hundreds of decision trees and averages their votes. | Hugely improves accuracy and stability over a single tree. |
| **Bagging** | "Bootstrap Aggregating". Training each tree on a slightly different, random subset of data. | Prevents overfitting. The errors of individual trees cancel out. |
| **n_estimators** | The total number of trees inside the forest. | More trees = better performance, but slower to train. |
| **feature_importances_** | Ranks how useful each column was across all the trees. | Helps identify which data is driving business outcomes. |

---

### 2. Scenario Analysis: Why use a Forest instead of a Tree?

* **1) Single Decision Tree (The Solo Expert):** Imagine asking one doctor to diagnose a rare disease. They might be biased by their specific past experiences and make a confident, but wrong, prediction. This is **High Variance (Overfitting)**.
* **2) Random Forest (The Expert Panel):** Imagine asking 100 different doctors. They all look at slightly different parts of the patient's chart. When they vote on the final diagnosis, the result is incredibly robust and reliable.

---

### 3. Algorithm Workflow (Bagging)

```text
┌─────────────────┐
│ Original Dataset│ ➔ 10,000 Flipkart Products.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Random Subsets │ ➔ Create 100 different mini-datasets by randomly picking rows.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Train 100 Trees │ ➔ Every tree learns slightly different rules (some look at Price, some at Rating).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Majority Vote  │ ➔ For a new product, all 100 trees vote. The category with the most votes wins!
└─────────────────┘
```

---

### 4. Tuning Parameters: Balancing Speed and Accuracy

* **More isn't always perfectly better:** Increasing `n_estimators` from 10 to 100 usually provides a massive jump in accuracy. But increasing it from 1,000 to 10,000 might only give a 0.01% boost while taking 10x longer to train.
* **Controlling Depth:** Setting `max_depth` ensures that the individual trees don't become massive, slow memory hogs.
