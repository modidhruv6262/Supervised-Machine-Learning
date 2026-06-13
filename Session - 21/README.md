# Time Series - Session 21

### 1. Feature Engineering for Time Series

| Concept | Explanation | Example Use Case |
| :--- | :--- | :--- |
| **Lag Features** | Copying data from *X* days ago into a new column. | Using the stock price from exactly 3 days ago as a hint for tomorrow's price. |
| **Rolling Features** | Calculating an average/sum over a window of *X* days. | Using the 7-day average sales to predict how busy a restaurant will be today. |
| **Temporal Features** | Extracting distinct units of time (Month, Day, Weekend) from a raw Date column. | Giving a model a simple `Is_Weekend` boolean instead of forcing it to figure out calendar math. |

---

### 2. Scenario Analysis: Regression Metrics Battle

* **MAE (The Compassionate Judge):** Takes the absolute difference between your prediction and reality. It treats all errors equally. If you are off by 5 degrees, it adds exactly 5 to your penalty.
* **RMSE (The Strict Judge):** Squares the errors before averaging them. If you are off by 1 degree, penalty = 1. But if you are off by 10 degrees, penalty = 100! **RMSE is hyper-sensitive to massive outliers.**
* **MAPE (The Percentage Judge):** Tells you the error in a clean percentage (e.g., "You are off by 5%"). Very easy for business leaders to understand, but it breaks mathmatically if your actual values hit `0`.

---

### 3. Algorithm Workflow (Random Forest on Time Series)

```text
┌─────────────────┐
│ Raw Dates       │ ➔ Oct 1st, Oct 2nd, Oct 3rd...
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Feature Engine  │ ➔ Create [Lag_3], [Rolling_7], [Is_Weekend]. Drop the actual Date.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Train RF Model  │ ➔ The Random Forest learns that [Is_Weekend=True] + [High Rolling_7] = Huge Sales!
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Future Forecast │ ➔ Feed the model tomorrow's Lag and Rolling data to get an instant prediction.
└─────────────────┘
```

---

### 4. Key Takeaways

* **Tree Models Hate Time:** Random Forests cannot inherently understand the concept of "time passing". You MUST use Feature Engineering (lags, rolling averages, temporal extraction) to convert time into static numbers the trees can actually understand!
* **SMAPE > MAPE:** When dealing with temperatures near 0, or sales that occasionally hit 0, always use **SMAPE**. Standard MAPE will throw a division-by-zero error or skyrocket to infinity.
