# Task 4 · Sentiment Analysis

A complete machine learning system to classify tweets as **positive**, **neutral**, or **negative** using natural language processing (NLP) preprocessing, TF-IDF feature extraction, Multinomial Naive Bayes, and Logistic Regression.

---

## Project Overview

Social media platforms like Twitter (X) are rich sources of customer sentiment, feedback, and brand perception. This project builds and evaluates an end-to-end NLP classification pipeline using the US Airline Sentiment dataset. The objective is to accurately categorize tweets into three sentiment classes, analyze model performance through comprehensive metrics, visualize class-specific vocabulary using WordClouds, and conduct error analysis to understand common misclassifications (such as sarcasm and mixed sentiment).

---

## Dataset

* **File Name:** `Tweets.csv`
* **Target Column:** `airline_sentiment` (contains `positive`, `neutral`, and `negative` classes)
* **Features:** Raw tweet text along with metadata (preprocessed for NLP feature extraction).

---

## Key Features & Pipeline Steps

1. **Text Preprocessing:**
   * Lowercasing text and removing URLs (`http/www`), user mentions (`@user`), hashtags (`#`), punctuation, and numbers.
   * Tokenization using regular expressions.
   * Stopword removal using NLTK English stopwords.
   * Lemmatization via WordNet Lemmatizer to reduce words to their root forms.

2. **Feature Extraction:**
   * **TF-IDF (Term Frequency–Inverse Document Frequency):** Converts text into numerical feature vectors (`max_features=15000`, unigrams and bigrams `ngram_range=(1,2)`, `min_df=2`, sublinear TF scaling).

3. **Machine Learning Models:**
   * **Multinomial Naive Bayes (`MultinomialNB`)**
   * **Logistic Regression (`LogisticRegression`, `max_iter=1000`)**

4. **Evaluation & Visualization:**
   * Metrics: Accuracy, Precision, Recall, and Weighted F1-Score.
   * Confusion Matrices for both models using seaborn heatmaps.
   * Sentiment-specific WordClouds to visualize high-frequency terms.
   * Error analysis highlighting misclassified samples and examining failure modes (e.g., sarcasm, context ambiguity).

---

## Requirements & Installation

Make sure you have Python 3.8+ installed along with the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn nltk wordcloud
```

Additionally, download the necessary NLTK corpora inside Python:
```python
import nltk
nltk.download("stopwords")
nltk.download("wordnet")
nltk.download("omw-1.4")
```

---

## Project Structure

```text
├── Tweets.csv              # Dataset (place in root directory)
├── sentiment_analysis.ipynb # Jupyter notebook containing full code and execution
└── README.md               # Project documentation
```

---

## Usage Instructions

1. Place `Tweets.csv` in the same directory as the Jupyter Notebook.
2. Open the notebook or execute the script cells sequentially:
   ```bash
   jupyter notebook sentiment_analysis.ipynb
   ```
3. Review the data inspection, preprocessing outputs, training metrics, confusion matrices, and error analysis sections.

---

## Real-World Applications

* **Customer Feedback Monitoring:** Automatically triage incoming customer complaints and praise.
* **Brand Reputation Tracking:** Assess real-time public sentiment during product launches or PR events.
* **Social Media Analytics:** Track customer satisfaction trends across different airline services over time.
* **Customer Support Prioritization:** Route negative tweets directly to priority support queues.

---

## Submission Notes

* Keep `Tweets.csv` in the working directory alongside the notebook.
* Ensure an 80/20 stratified train/test split is maintained (`random_state=42`).
* Inspect all evaluation metrics, confusion matrices, WordClouds, and error examples prior to final submission.
