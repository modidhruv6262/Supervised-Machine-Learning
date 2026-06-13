# Classification Algorithms Part 3 - Assignment 12

### 1. Decision Trees Concepts

| Concept | Explanation | Real-World Impact |
| :--- | :--- | :--- |
| **Decision Tree Classifier** | An algorithm that splits data based on series of yes/no questions. | Intuitive to understand and visualize (like a flowchart). |
| **Gini Impurity** | Measures how often a randomly chosen element would be incorrectly labeled. | Default metric; very fast for the tree to compute. |
| **Entropy** | Measures the level of "disorder" or information gain in a split. | Computationally slightly heavier (logarithms), but produces balanced trees. |
| **Max Depth** | The maximum number of levels/splits the tree is allowed to make. | Prevents the tree from overfitting by stopping it from memorizing data. |

---

### 2. Scenario Analysis: To Prune or Not To Prune?

* **1) High-Stakes Financial Fraud (No Pruning?):** You might be tempted to let a tree grow infinitely deep to catch every tiny detail. However, this causes **overfitting**. The tree memorizes the training data but fails completely on new, real-world credit card transactions.
* **2) Medical Triage (Pruning / Max Depth):** Limiting `max_depth=3` forces the tree to find the 3 most critical rules (e.g., Heart Rate > 120, Age > 60). It creates a generalized, readable rule set that doctors can actually trust and verify on a clipboard.

---

### 3. Algorithm Workflow (Decision Tree Split)

```text
┌─────────────────┐
│  Root Dataset   │ ➔ All IPL Matches (Wins & Losses mixed).
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Best Condition  │ ➔ The tree tests all columns and finds 'Team Runs > 160'
│   (Gini/Ent)    │   separates Wins and Losses best.
└─────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌───────┐ ┌───────┐
│ Node A│ │ Node B│ ➔ Data is split into two cleaner child nodes.
└───────┘ └───────┘
         │
         ▼
┌─────────────────┐
│  Leaf (Pure)    │ ➔ Process repeats until max_depth is hit or nodes are pure.
└─────────────────┘
```

---

### 4. Feature Importance Insights

* **The "Why":** Decision trees don't just give you a prediction; they give you a ranking of `feature_importances_`.
* **Example in Iris Dataset:** It mathematically proves that `petal length` and `petal width` are far more useful for identifying the flower species than `sepal length` and `sepal width`. This is incredibly valuable for businesses deciding which data points to prioritize collecting!
