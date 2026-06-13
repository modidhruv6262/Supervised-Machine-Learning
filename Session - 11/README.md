# Classification Algorithms Part 2 - Assignment 11

### 1. Classification Models & Use Cases

| Dataset Context | Target Prediction | Algorithm Used | Key Concept |
| :--- | :--- | :--- | :--- |
| **Flipkart Reviews** | Positive / Negative | K-Nearest Neighbors (KNN) | Text Vectorization (`CountVectorizer`) |
| **Spotify Features** | Workout / Chill | K-Nearest Neighbors (KNN) | Distance Metrics (Euclidean vs Manhattan) |
| **IRCTC Bookings** | Confirmed / Waitlisted | Gaussian Naive Bayes | Continuous feature probabilities |
| **WhatsApp Chats** | Personal / Group / Spam | Multinomial Naive Bayes | Text classification & Confusion Matrix |
| **Sports Images** | Cricket Bat / Football | K-Nearest Neighbors (KNN) | 2D Image Flattening |

---

### 2. Scenario Analysis: Distance Metrics in KNN

* **1) Euclidean Distance (Straight Line):** Best for continuous, dense features like physical distance or audio frequencies (e.g., Spotify acoustic properties).
* **2) Manhattan Distance (City Block):** Best for grid-like movement or high-dimensional sparse data (e.g., counting words in reviews).

---

### 3. Naive Bayes Classification Workflow (WhatsApp Spam Example)

```text
┌─────────────────┐
│  Text Messages  │ ➔ Raw text from WhatsApp chats.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Vectorization   │ ➔ CountVectorizer turns words into frequency numbers.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Probability   │ ➔ MultinomialNB calculates probability of Spam given words.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Prediction    │ ➔ Assigns highest probability label (Personal/Group/Spam).
└─────────────────┘
```

---

### 4. Code Debugging Insights (AI Generated Code)

* **Common AI Mistake:** Image arrays are inherently 3D (samples, height, width), but Scikit-learn models expect 2D arrays (samples, features).
* **The Fix:** Using `.reshape(n_samples, -1)` to flatten images into a 1D sequence of pixels before passing them into the KNN `.fit()` method.
