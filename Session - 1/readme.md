# Intro to Machine Learning - Assignment 01

### 1. App Features & ML Classifications

| Application | Feature Name | ML Paradigm Type |
| :--- | :--- | :--- |
| **Instagram** | Explore Page | Supervised Learning |
| **Zomato** | Delivery ETA Prediction | Supervised Learning |
| **Flipkart** | Product Recommendations | Unsupervised Learning |

---

### 2. Scenario Analysis

* **1) Netflix Movie Recommendations:** Supervised Learning (Uses labeled watch history to predict preferences).
* **2) Spotify Playlist Grouping:** Unsupervised Learning (Clusters similar tracks without category labels).
* **3) Self-Driving Car Parking:** Reinforcement Learning (Learns maneuvers via environmental rewards and penalties).

---

### 3. Machine Learning Workflow (Swiggy Example)

```text
┌─────────────────┐
│      Data       │ ➔ Collects delivery history, traffic, and coordinates.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Preprocessing  │ ➔ Cleans data and removes incomplete records.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│    Modeling     │ ➔ Trains a regression model to predict delivery times.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Evaluation    │ ➔ Tests predictions against real delivery times.
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Deployment    │ ➔ Pushes the model live to display real-time ETAs.
└─────────────────┘
```

---

### 4. Traditional Programming vs. Machine Learning

* **Traditional Programming:** Requires explicit manual rules (e.g., blocking the exact word "lottery"). If spammers change the spelling to "l0ttery," the code breaks until updated manually.
* **Machine Learning:** Automatically learns patterns from labeled data. It analyzes examples of spam and non-spam to adapt to new tricks without manual code updates.
