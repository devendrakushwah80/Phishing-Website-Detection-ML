# 🛡️ Phishing Website Detection using Machine Learning

This project focuses on detecting **phishing websites** using classical machine learning techniques.  
The dataset consists of **binary features (-1, 1)** representing various characteristics of a website.

The goal is to classify websites as **phishing** or **legitimate** based on these features.

---

## 📌 Problem Statement

Phishing websites mimic legitimate websites to steal sensitive user information such as login credentials and financial data.  
This project aims to build a **machine learning-based classification system** to automatically detect phishing websites.

---

## 📊 Dataset Overview

- **Dataset File**: `phishing.csv`
- **Target Column**: `class`
  - `1` → Legitimate website
  - `-1` → Phishing website

### Feature Characteristics
- All features are **numerical and binary (-1, 1)**
- No missing values
- No duplicate records
- No categorical encoding required
- Feature scaling not required

### Example Features
- UsingIP
- LongURL
- ShortURL
- PrefixSuffix-
- HTTPS
- DomainRegLen
- GoogleIndex
- PageRank
- WebsiteTraffic
- LinksPointingToPage
- StatsReport

---

## 🔍 Exploratory Data Analysis (EDA)

The following checks and visualizations were performed:

- Dataset shape and structure
- Data types verification
- Missing value check
- Duplicate row detection
- Unique value distribution per feature
- Feature-wise class distribution using `seaborn.countplot`

EDA confirmed that the dataset is **clean, balanced, and model-ready**.

---

## 🧠 Machine Learning Models Used

### 1️⃣ Logistic Regression
- Used as a baseline linear classifier
- `max_iter=1000` for stable convergence
- Provides interpretability and strong baseline performance

### 2️⃣ Support Vector Machine (SVM)
- Kernel: **RBF**
- `probability=True` enabled
- Effective for capturing non-linear decision boundaries

### 3️⃣ K-Nearest Neighbors (KNN)
- Distance-based classifier
- Performance evaluated for multiple values of **K**
- Best K selected based on evaluation metrics

---

## ✂️ Train-Test Split

```python
train_test_split(
    X, y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```
80% Training data

20% Testing data

Stratification preserves class balance
📈 Model Evaluation Metrics

Each model was evaluated using:

Accuracy

Precision

Recall

F1-Score

ROC–AUC Score

ROC–AUC was used as a primary comparison metric.

🏆 Model Performance Comparison
Model	Accuracy	ROC–AUC
Logistic Regression	High	High
SVM (RBF Kernel)	High	High
KNN	High	High
🔧 KNN Hyperparameter Tuning

Tested multiple values of K

Stored results in a DataFrame

Ranked models based on performance

Selected the best K value

best_k = knn_results.sort_values(
    by=["ROC_AUC", "Accuracy"],
    ascending=False
).iloc[0]["K"]

📂 Project Structure
Phishing-Website-Detection-ML/
│
├── phishing.csv
├── phishing_website_detection.ipynb
├── README.md
├── requirements.txt
