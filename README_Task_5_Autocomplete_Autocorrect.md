# TASK 5 · Autocomplete and Autocorrect Data Analytics

## NLP-Based Text Prediction and Spelling Correction

### Project Overview

This project analyses the efficiency and accuracy of autocomplete and autocorrect algorithms using Natural Language Processing (NLP).

The notebook builds frequency-based **bigram and trigram models** for autocomplete and uses **pyspellchecker / edit-distance-based correction** for autocorrect.

### Objectives

- Collect a large text corpus.
- Perform NLP preprocessing.
- Build bigram and trigram autocomplete models.
- Test autocomplete on at least 10 input prefixes.
- Display the top 3 predictions for each prefix.
- Implement edit-distance-based autocorrection.
- Test 20 deliberately misspelled words.
- Calculate autocomplete Precision and Recall.
- Calculate autocorrect Precision, Recall and Accuracy.
- Compare two autocomplete approaches.
- Visualise the top 20 frequent words.
- Generate an autocorrection confusion matrix.
- Discuss limitations compared with production systems such as Google Keyboard.

---

## Dataset

### Project Gutenberg Corpus

This project uses the **Project Gutenberg** collection as its text corpus.

Project Gutenberg provides thousands of free public-domain ebooks and makes the books available as plain-text files.

**Official website:**  
https://www.gutenberg.org/

**Official download / catalogue:**  
https://www.gutenberg.org/ebooks/

**All plain-text files information:**  
https://dev.gutenberg.org/ebooks/offline_catalogs.html

The notebook uses the **NLTK Gutenberg corpus**, so you do not need to manually download a huge dataset. When the notebook runs:

```python
nltk.download("gutenberg")
```

the required corpus is downloaded automatically.

The notebook combines the available Gutenberg books into one text corpus.

---

## Dataset Characteristics

The Gutenberg corpus contains multiple books and therefore provides a much larger vocabulary and number of word sequences than a small sample text.

The exact number of tokens processed can vary depending on the version of the NLTK corpus.

The corpus is mainly literary/public-domain English text, so it is useful for demonstrating NLP techniques but does not perfectly represent modern chat or mobile-keyboard language.

---

## Project Structure

```text
Task-5 Autocomplete and Autocorrect/
│
├── Task_5_Autocomplete_Autocorrect_NLP.ipynb
│
└── README.md
```

No separate CSV file is required because the notebook downloads the NLTK Gutenberg corpus automatically.

---

## Tech Stack

- Python
- Jupyter Notebook
- pandas
- NumPy
- NLTK
- pyspellchecker
- collections
- matplotlib
- seaborn

---

## NLP Preprocessing

The notebook performs:

1. Tokenisation
2. Lowercasing
3. Punctuation removal
4. Stopword removal

For autocomplete, stopwords are retained in the n-gram sequence because words such as `the`, `of`, `to`, and `is` are important for natural next-word prediction.

Stopword removal is used for the general word-frequency analysis.

---

## Autocomplete

Two frequency-based approaches are implemented.

### Bigram Model

A bigram uses one previous word to predict the next word.

Example:

```text
Input: "in the"
Context: "the"
Prediction: next word
```

### Trigram Model

A trigram uses the previous two words.

Example:

```text
Input: "in the house"
Context: "the house"
Prediction: next word
```

The notebook displays the **top 3 predictions** for more than 10 test prefixes.

---

## Autocomplete Evaluation

The notebook calculates:

### Precision@3

Measures how many of the three returned predictions are relevant.

### Recall@3

Measures whether the actual next word appears within the top 3 predictions.

These metrics allow the bigram and trigram models to be compared objectively.

---

## Autocorrect

The project uses `pyspellchecker` for spelling correction.

Twenty deliberately misspelled words are tested, including examples such as:

```text
teh → the
recieve → receive
definately → definitely
becuase → because
adress → address
acheive → achieve
```

The notebook compares the predicted correction with the intended word.

---

## Autocorrect Evaluation

The notebook calculates:

- Accuracy
- Precision
- Recall
- Number of correct corrections
- Number of incorrect corrections
- Levenshtein distance

A confusion matrix is also generated to show correct versus incorrect corrections.

---

## Visualisations

The notebook creates:

1. **Top 20 most frequent words bar chart**
2. **Autocomplete model comparison chart**
3. **Autocorrect confusion matrix**

---

## Algorithm Comparison

| Model | Context | Advantage | Limitation |
|---|---|---|---|
| Bigram | 1 previous word | Fast and simple | Limited context |
| Trigram | 2 previous words | More contextual | More sparse/unseen combinations |

The notebook compares both approaches using Precision@3 and Recall@3.

---

## Limitations Compared with Google Keyboard

This project is a simplified educational implementation.

Production autocomplete/autocorrect systems can use:

- Neural language models
- Transformer-based models
- Much larger training datasets
- Long-range context
- User-specific vocabulary
- Personal writing style
- Keyboard proximity information
- Sentence-level semantic understanding
- Multilingual models
- Emoji and slang understanding
- Real-time learning
- Extremely low-latency inference
- Large-scale privacy-aware systems

The Gutenberg corpus also contains mostly literary/public-domain text, so it does not fully represent modern texting, social media, technical terms, names, abbreviations, or Indian English.

---

## How to Run

### 1. Open the notebook

Open:

```text
Task_5_Autocomplete_Autocorrect_NLP.ipynb
```

in VS Code or Jupyter Notebook.

### 2. Install required packages

Run:

```bash
pip install nltk pyspellchecker pandas numpy matplotlib seaborn
```

### 3. Download the corpus

The notebook automatically runs:

```python
nltk.download("gutenberg")
nltk.download("stopwords")
```

### 4. Run all cells

Run the notebook from top to bottom.

---

## References

1. Project Gutenberg  
   https://www.gutenberg.org/

2. Project Gutenberg Offline Catalogues / Plain Text Collection  
   https://dev.gutenberg.org/ebooks/offline_catalogs.html

3. NLTK Documentation  
   https://www.nltk.org/

4. NLTK Gutenberg Corpus  
   https://www.nltk.org/book/ch02.html

5. pyspellchecker Documentation  
   https://pyspellchecker.readthedocs.io/

6. Python Collections Documentation  
   https://docs.python.org/3/library/collections.html

---

## Feature Checklist

- [x] Large text corpus
- [x] Tokenisation
- [x] Lowercasing
- [x] Punctuation removal
- [x] Stopword removal
- [x] Bigram autocomplete
- [x] Trigram autocomplete
- [x] 10+ autocomplete test prefixes
- [x] Top 3 predictions
- [x] Edit-distance-based autocorrect
- [x] 20 misspelled words
- [x] Autocomplete Precision
- [x] Autocomplete Recall
- [x] Autocorrect Precision
- [x] Autocorrect Recall
- [x] Autocorrect Accuracy
- [x] Algorithm comparison
- [x] Top 20 frequent-word chart
- [x] Confusion matrix
- [x] Production-system limitations

---

## Conclusion

This project demonstrates the fundamental NLP techniques behind autocomplete and autocorrect.

Frequency-based n-gram models are simple, fast, and interpretable, while edit-distance-based spelling correction works well for many common typing mistakes. However, production systems require much richer context, personalisation, neural language models, large-scale data, and highly optimised inference.
