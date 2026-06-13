# Classification Evaluation Metrics Part 2 - Session 17

### 1. Advanced Metrics

| Metric | Explanation | Best Use Case |
| :--- | :--- | :--- |
| **ROC Curve** | Plots True Positive Rate vs False Positive Rate across all thresholds. | General-purpose model evaluation. |
| **AUC** | Area Under the Curve. 1.0 is perfect, 0.5 is a coin toss. | Comparing two models against each other. |
| **PR Curve** | Precision vs Recall across all thresholds. Ignores True Negatives. | Extremely imbalanced datasets (e.g., Fraud). |
| **Log Loss** | Penalizes the model if it's confidently wrong (e.g., 99% sure it's fraud, but it isn't). | When probability scores matter more than absolute classes. |

---

### 2. Scenario Analysis: Handling Imbalanced Data

* **The Credit Card Problem:** Imagine an Indian bank processes 1,000,000 transactions a day, and only 100 are fraud (0.01%). 
* **The Accuracy Trap:** If you use **Accuracy** as your metric, a broken AI that just labels *everything* as "Legit" will be 99.99% accurate. Your boss might be happy with the number, but millions of rupees will be stolen!
* **The Solution:** We ignore Accuracy entirely. We look at the **Precision-Recall Curve** and **F1 Score** because they force the model to prove that it can actually find those 100 fraudulent needles in the massive haystack of normal transactions.

---

### 3. Log Loss Workflow (Cross Entropy)

```text
┌─────────────────┐
│ AI Probability  │ ➔ The AI says "I am 99% sure this is Fraud."
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Actual Outcome  │ ➔ The transaction was actually NORMAL.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  High Penalty!  │ ➔ Log Loss massively penalizes the AI for being arrogantly wrong.
└─────────────────┘
```

---

### 4. Key Takeaways

* **ROC vs PR:** If the negative class (normal stuff) is huge and you don't care about it, drop the ROC curve and use the Precision-Recall curve instead.
* **Confidence Matters:** Log Loss ensures your model isn't just making the right choices, but making them with appropriate levels of humility and confidence.
