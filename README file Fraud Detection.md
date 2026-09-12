# TASK 3 · Fraud Detection

## Credit Card Fraud Detection Using Machine Learning and SMOTE

### 📌 Project Overview

This project builds a machine learning pipeline to detect fraudulent
financial transactions from a highly imbalanced credit card transaction
dataset.

The main challenge is **class imbalance** because fraudulent
transactions represent only a very small percentage of all transactions.
The project addresses this problem using **SMOTE (Synthetic Minority
Over-sampling Technique)** and evaluates models using fraud-focused
metrics rather than relying only on accuracy.

------------------------------------------------------------------------

## 🎯 Objective

-   Analyse class imbalance and calculate the percentage of fraudulent
    transactions.
-   Perform EDA on transaction amounts and time-of-day patterns.
-   Explain why accuracy is misleading for imbalanced fraud datasets.
-   Use **SMOTE** to handle class imbalance.
-   Perform a stratified train/test split.
-   Train **Logistic Regression** and **Random Forest** models.
-   Evaluate using Precision, Recall, F1-Score, and ROC-AUC.
-   Analyse feature importance / coefficients.
-   Discuss scalability to approximately 1 million transactions per
    hour.

------------------------------------------------------------------------

## 📊 Dataset

The project uses the **Credit Card Fraud Detection** dataset from
Kaggle.

-   Total transactions: **284,807**
-   Legitimate transactions: **284,315**
-   Fraudulent transactions: **492**
-   Fraud percentage: approximately **0.172%**
-   Features: **30**
-   Target column: `Class`

  Class   Meaning
  ------- ------------------------
  `0`     Legitimate transaction
  `1`     Fraudulent transaction

**Dataset:** https://www.kaggle.com/mlg-ulb/creditcardfraud

------------------------------------------------------------------------

## 🛠️ Tech Stack

-   Python
-   Jupyter Notebook
-   pandas
-   NumPy
-   scikit-learn
-   imbalanced-learn
-   SMOTE
-   matplotlib
-   seaborn

------------------------------------------------------------------------

## 📁 Project Structure

``` text
Task-4 Fraud Detection/
│
├── Fraud Dataset/
│   └── creditcard.csv
│
├── OIBSIP.Data_Analytics_Fraud_Detection_SMOTE.ipynb
│
└── README.md
```

Keep `creditcard.csv` inside the **Fraud Dataset** folder when running
the notebook.

------------------------------------------------------------------------

## 🔍 Exploratory Data Analysis

### Class Distribution

The dataset is extremely imbalanced. Only about **0.172%** of
transactions are fraudulent.

### Transaction Amount

The notebook compares transaction amounts for legitimate and fraudulent
transactions and also uses a log-scaled view because transaction amounts
are highly skewed.

### Time-of-Day

The `Time` column represents elapsed seconds from the first transaction.
The notebook converts it into a relative hour-of-day representation for
exploratory analysis.

------------------------------------------------------------------------

## ⚠️ Why Accuracy Is Misleading

Accuracy can be misleading because legitimate transactions dominate the
dataset.

A classifier predicting every transaction as legitimate could achieve
approximately **99.83% accuracy while detecting zero fraud cases**.

Therefore, the project focuses on:

-   **Precision** --- how many predicted fraud cases are actually fraud.
-   **Recall** --- how many actual fraud cases are detected.
-   **F1-Score** --- balance between precision and recall.
-   **ROC-AUC** --- ability to separate/rank fraud and legitimate
    transactions across thresholds.

------------------------------------------------------------------------

## ⚖️ Handling Class Imbalance with SMOTE

**SMOTE (Synthetic Minority Over-sampling Technique)** creates synthetic
minority-class examples using existing minority samples and their
neighbours.

The notebook applies SMOTE **only to the training data**.

Correct workflow:

``` text
Original Dataset
       ↓
Stratified Train/Test Split
       ↓
Training Data → Scaling → SMOTE → Model Training
Test Data     → Scaling → Final Evaluation
```

The test set is never oversampled, so final evaluation remains
representative of the original class distribution.

------------------------------------------------------------------------

## 🤖 Machine Learning Models

### 1. Logistic Regression

Used as an interpretable baseline for binary classification. Its
coefficients are also analysed to understand feature influence.

### 2. Random Forest

An ensemble of decision trees capable of modelling nonlinear
relationships. Random Forest feature importance is analysed after
training.

------------------------------------------------------------------------

## 📈 Evaluation

The models are evaluated using:

  Metric      Purpose
  ----------- --------------------------------------------
  Precision   Measures correctness of fraud alerts
  Recall      Measures how much actual fraud is detected
  F1-Score    Balances Precision and Recall
  ROC-AUC     Measures ranking/separation performance
  Accuracy    Shown only for context

The notebook also generates confusion matrices and ROC curves.

------------------------------------------------------------------------

## 🚨 Recall vs Precision

For many fraud detection systems, **Recall is especially important**
because a false negative means an actual fraudulent transaction was
missed.

However, maximizing recall can increase false positives. High precision
reduces unnecessary fraud alerts but may allow some fraud to pass.

Therefore, the production threshold should be selected according to the
business cost of:

-   Missed fraud / false negatives
-   False alarms / false positives

Precision, Recall, F1-Score and ROC-AUC should therefore be considered
together.

------------------------------------------------------------------------

## 🔬 Feature Analysis

### Logistic Regression

The notebook examines coefficient magnitude and direction. Positive
coefficients push predictions toward fraud, while negative coefficients
push them toward legitimate transactions.

### Random Forest

Random Forest feature importance is used to identify variables that
contributed most to the model's predictions.

Feature importance indicates predictive usefulness and should not
automatically be interpreted as causation.

------------------------------------------------------------------------

## 🚀 Scalability --- 1 Million Transactions per Hour

Processing **1,000,000 transactions per hour** is approximately **278
transactions per second** on average.

A production architecture could use:

1.  Streaming ingestion such as Kafka, Kinesis, or Pub/Sub.
2.  A real-time feature service.
3.  Low-latency model serving.
4.  Multiple model-serving instances behind a load balancer.
5.  Continuous monitoring of fraud rate, Recall, Precision, latency, and
    data drift.
6.  Periodic retraining using recent labelled transactions.
7.  Risk-based thresholds for blocking, allowing, or manually reviewing
    transactions.

**Important:** SMOTE is a training-time technique. It is not applied to
live transactions.

------------------------------------------------------------------------

## ▶️ How to Run

### 1. Download the dataset

Download `creditcard.csv` from:

https://www.kaggle.com/mlg-ulb/creditcardfraud

### 2. Place the CSV

Put it here:

``` text
Fraud Dataset/
    creditcard.csv
```

### 3. Open the notebook

Open:

``` text
OIBSIP.Data_Analytics_Fraud_Detection_SMOTE.ipynb
```

in VS Code or Jupyter Notebook.

### 4. Install dependencies

``` bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn jupyter
```

### 5. Run

Run the notebook cells from top to bottom.

------------------------------------------------------------------------

## 📚 References

1.  Kaggle --- Credit Card Fraud Detection\
    https://www.kaggle.com/mlg-ulb/creditcardfraud

2.  imbalanced-learn --- SMOTE Documentation\
    https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html

3.  Chawla, N. V., Bowyer, K. W., Hall, L. O., & Kegelmeyer, W. P.
    (2002). *SMOTE: Synthetic Minority Over-sampling Technique*. Journal
    of Artificial Intelligence Research.

4.  YouTube --- Fraud Detection / Imbalanced Dataset / SMOTE tutorials\
    https://www.youtube.com/

------------------------------------------------------------------------

## ✅ Project Checklist

-   [x] Load dataset and analyse class imbalance
-   [x] Calculate fraudulent transaction percentage
-   [x] EDA: transaction amounts
-   [x] EDA: time-of-day analysis
-   [x] Explain misleading accuracy
-   [x] Stratified train/test split
-   [x] Apply SMOTE
-   [x] Logistic Regression
-   [x] Random Forest
-   [x] Precision
-   [x] Recall
-   [x] F1-Score
-   [x] ROC-AUC
-   [x] ROC curve
-   [x] Confusion matrices
-   [x] Feature coefficient analysis
-   [x] Random Forest feature importance
-   [x] Recall vs Precision discussion
-   [x] Scalability discussion

------------------------------------------------------------------------

## 🏁 Conclusion

This project demonstrates an end-to-end fraud detection workflow under
severe class imbalance.

The main takeaway is that **high accuracy does not necessarily mean a
good fraud detection model**. A practical fraud detection system should
catch genuine fraud while keeping false alerts manageable. SMOTE,
stratified splitting, Logistic Regression, Random Forest, and
fraud-focused evaluation metrics provide a strong foundation for this
task.
