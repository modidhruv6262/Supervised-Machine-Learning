  # Intro to Machine Learning Part 2 - Assignment 02

### 1. Data Splitting & Regression Analysis

| Dataset Concept | ML Operation | Purpose |
| :--- | :--- | :--- |
| **Spotify Top 50 Songs** | Loading & Inspection | Understanding feature distribution (e.g. Danceability vs Popularity) |
| **Train/Test Split** | `train_test_split` | Preventing the model from memorizing data; evaluating true performance |
| **Linear Regression** | Trend Line Fitting | Predicting a continuous target (Song Popularity) from an input feature |

---

### 2. Scenario Analysis: Overfitting in the Real World

* **1) Social Media Feeds (Overfitting):** If an algorithm perfectly memorizes that you liked one video about cats and suddenly only shows you cat videos, it has overfit to a tiny sample and fails to generalize your broader interests.
* **2) Navigation Apps (Underfitting):** If a GPS ignores all real-time traffic and only assumes every trip takes the exact speed limit, it is underfitting the complexity of real-world driving.

---

### 3. Machine Learning Workflow (Spotify Example)

```text
┌─────────────────┐
│  Raw CSV Data   │ ➔ Load Kaggle Spotify Top 50 dataset.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Data Splitting  │ ➔ 80% to train the model, 20% held back to test it.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Model Training  │ ➔ Fit a Linear Regression line to Danceability & Popularity.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Evaluation    │ ➔ Check predictions on the 20% test set to catch overfitting.
└─────────────────┘
```

---

### 4. Bias-Variance Tradeoff

* **High Bias (Underfitting):** The model is too simple (e.g., a straight line through a curved dataset). It makes strong, incorrect assumptions.
* **High Variance (Overfitting):** The model is too complex. It connects every single dot perfectly but fails when given new data.
* **The Goal:** Find the sweet spot in the middle where the model captures the underlying pattern without memorizing the noise.
