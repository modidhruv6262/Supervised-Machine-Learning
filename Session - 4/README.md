# Data Processing Part 2 - Assignment 04

### 1. Scaling & Feature Selection Methods

| Technique | Goal | Application Example |
| :--- | :--- | :--- |
| **StandardScaler** | Center data around 0 with standard deviation 1 | IPL Stats (Runs vs Strike Rate) |
| **MinMaxScaler** | Compress data into a fixed range [0, 1] | Flipkart Ratings (1-5) and Prices (₹₹₹) |
| **Correlation Analysis** | Find how strongly features relate to target | Spotify Popularity Predictors |
| **RFE (Recursive Feature Elimination)** | Automatically drop the weakest features | Zomato Restaurant Rating model |
| **IQR Method** | Detect and handle statistical outliers | BookMyShow highly skewed ratings |

---

### 2. Scenario Analysis: Why Scale Data?

* **1) K-Nearest Neighbors (KNN):** KNN calculates distance. If Flipkart Price is in thousands and Rating is 1-5, the Price will mathematically dominate the distance calculation. Scaling puts them on equal footing.
* **2) Gradient Descent Speed:** Algorithms like Neural Networks and Logistic Regression converge much faster and safely when data is scaled. Unscaled data causes bouncing and slow learning.

---

### 3. Feature Selection Workflow (Zomato Example)

```text
┌─────────────────┐
│ All Features (10)│ ➔ Model uses Location, Price, Cuisines, Votes, etc.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Train Algorithm │ ➔ Train a Decision Tree to predict Restaurant Rating.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Rank Importance │ ➔ Identify the least important feature (e.g., 'Has TV').
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Drop & Repeat   │ ➔ Remove it and repeat until the optimal subset is found.
└─────────────────┘
```

---

### 4. Outliers and IQR (Interquartile Range)

* **Definition:** An outlier is a data point drastically different from the rest (e.g., a movie with 1 million fake 5-star ratings).
* **IQR Logic:** Calculate the middle 50% of data (Q3 - Q1). Anything falling far below Q1 or far above Q3 (usually by 1.5 * IQR) is flagged as an outlier to be removed or capped.
