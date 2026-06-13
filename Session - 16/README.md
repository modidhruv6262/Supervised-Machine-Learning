# Classification Evaluation Metrics Part 1 - Session 16

### 1. Confusion Matrix Metrics

| Metric | Formula | What it answers |
| :--- | :--- | :--- |
| **Accuracy** | (TP + TN) / Total | Out of all predictions, how many were perfectly correct? |
| **Precision** | TP / (TP + FP) | Out of all the times the model yelled "Positive!", how often was it actually right? |
| **Recall** | TP / (TP + FN) | Out of all the actual Positive cases out there, how many did the model manage to catch? |
| **F1 Score** | Harmonic Mean of P & R | How well is the model balancing Precision and Recall without failing at one? |

---

### 2. Scenario Analysis: Precision vs Recall

* **1) Fake News Detection (Focus on Precision):** If a social media platform flags too many real posts as "Fake News", users will get angry and leave. We want high **Precision** (only flag it if we are 100% sure it's fake).
* **2) Disease Screening (Focus on Recall):** If an AI screens for a fatal illness, we absolutely cannot afford to miss a sick person (False Negative). We want high **Recall** (catch everyone who might be sick, even if it means doing a few unnecessary extra tests on healthy people).
* **3) Food Delivery Fraud (Focus on F1 Score):** Banning fake users is important, but banning real paying customers is bad. We need a perfect balance. The **F1 Score** measures this balance perfectly.

---

### 3. Confusion Matrix Workflow (Spam Filter)

```text
                 Predicted: SPAM      Predicted: NORMAL
               ┌────────────────────┬────────────────────┐
               │                    │                    │
Actual: SPAM   │ True Positive (TP) │ False Negative (FN)│
               │   (Spam Caught!)   │   (Spam Leaked!)   │
               ├────────────────────┼────────────────────┤
               │                    │                    │
Actual: NORMAL │ False Positive (FP)│ True Negative (TN) │
               │ (Real mail blocked)│ (Real mail passed) │
               └────────────────────┴────────────────────┘
```

---

### 4. Key Takeaways

* **The Accuracy Trap:** If you have an app where 99% of transactions are normal and 1% is fraud, a model that simply guesses "Normal" every single time will be 99% accurate! But it is completely useless.
* **The Solution:** We look at the confusion matrix instead. Precision, Recall, and F1-score immediately expose "lazy" models that just predict the majority class.
