# Model Evaluation & Improvement Part 1 - Session 18

### 1. Cross-Validation Concepts

| Concept | Explanation | Real-World Benefit |
| :--- | :--- | :--- |
| **Train/Test Split** | Slicing data into two pieces (e.g. 80/20) one time. | Fast, but prone to luck. What if the 20% test slice happens to be super easy? |
| **K-Fold Cross Validation** | Slicing data into *K* chunks. Training on K-1, testing on 1. Repeating until every chunk has been tested. | Guarantees the AI is tested on 100% of the data eventually. Prevents "lucky" accuracy scores. |
| **Stratified K-Fold** | The same as K-Fold, but guarantees every chunk has the exact same ratio of classes (e.g., 90% normal, 10% fraud). | Prevents a catastrophic fold where the AI accidentally trains on 0 fraud cases. |
| **Standard Deviation** | A measure of how much the accuracy jumps around between folds. | Tells you if your model is stable or heavily reliant on specific rows of data. |

---

### 2. Scenario Analysis: Why is K-Fold Better?

* **The "Lucky Split" Problem:** Imagine training a student for an exam. You give them 80 practice questions and test them on 20. If they score 100%, is it because they are smart, or because those 20 test questions just happened to be their favorite topic? 
* **The K-Fold Solution:** K-Fold CV makes the student take the test 5 different times, with a completely different set of 20 questions each time. If they average 95% across all 5 tests, you have mathematically proven they actually understand the material.

---

### 3. Algorithm Workflow (5-Fold CV)

```text
Dataset [■■■■■]

Fold 1: [TEST ] [Train] [Train] [Train] [Train] ➔ Score: 92%
Fold 2: [Train] [TEST ] [Train] [Train] [Train] ➔ Score: 89%
Fold 3: [Train] [Train] [TEST ] [Train] [Train] ➔ Score: 95%
Fold 4: [Train] [Train] [Train] [TEST ] [Train] ➔ Score: 90%
Fold 5: [Train] [Train] [Train] [Train] [TEST ] ➔ Score: 93%

➔ Final Model Accuracy = Average(91.8%)
```

---

### 4. Key Takeaways

* **Standard > Faster:** A basic `train_test_split` is great for quick prototyping, but `cross_val_score` is the absolute gold standard for proving your AI is ready for production.
* **Stratification is Mandatory:** If your dataset is imbalanced (e.g., churn prediction, fraud detection), you MUST use `StratifiedKFold`. Otherwise, a random fold might contain absolutely zero instances of the minority class, causing the model to crash or report misleading metrics.
