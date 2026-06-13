# Time Series Analysis - Session 20

### 1. Core Time Series Components

| Component | Explanation | Example |
| :--- | :--- | :--- |
| **Trend** | The long-term direction of the data over time. | Global warming slowly raising average yearly temperatures. |
| **Seasonality** | Predictable, repeating patterns at fixed intervals. | It gets hotter every summer and colder every winter. |
| **Residuals (Noise)** | Random, unpredictable fluctuations that don't fit the trend or season. | A sudden, unseasonal 2-day cold snap in the middle of summer. |

---

### 2. Scenario Analysis: Stationary vs Non-Stationary Data

* **Stationary Data (The Flat Road):** Imagine driving on an endless flat highway. The bumps in the road (data) go up and down randomly, but the average altitude never changes. Machine Learning models LOVE stationary data because the rules of the game never change.
* **Non-Stationary Data (The Mountain Climb):** Imagine driving up a mountain. Not only are there bumps, but your average altitude is constantly rising. Time series models (like ARIMA) struggle with this, which is why we often use "Differencing" to flatten the mountain back into a road before forecasting.

---

### 3. ARIMA Model Workflow

```text
┌─────────────────┐
│ Past Data (Y)   │ ➔ We look at the past 7 days of temperatures in New Delhi.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ AR (AutoRegress)│ ➔ "Tomorrow's temp will probably be like yesterday's temp." (p parameter)
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ I (Integration) │ ➔ "Let's subtract today from yesterday to flatten the trend!" (d parameter)
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ MA (Moving Avg) │ ➔ "Let's correct our prediction based on recent errors." (q parameter)
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ FORECAST        │ ➔ Predicts the next 7 days with mathematical confidence!
└─────────────────┘
```

---

### 4. Key Takeaways

* **ADF Test is crucial:** You cannot blindly throw data into an ARIMA model. You must use the **Augmented Dickey-Fuller (ADF) Test** to mathematically prove if your data is stationary. If it isn't (p-value > 0.05), you must apply transformations like differencing or logs.
* **Smoothing hides the noise:** Using a 7-day Moving Average (MA) perfectly cuts out daily chaotic spikes, revealing the true underlying shape of the data.
