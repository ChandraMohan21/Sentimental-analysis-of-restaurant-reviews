# Restaurant Review Sentiment Classifier

A Flask web app that labels a restaurant review as **positive** or **negative**.

## How it works

1. **Data:** `Restaurant_Reviews.tsv`, 1,000 labelled reviews (1 = positive, 0 = negative). Duplicates are dropped before training.
2. **Text cleaning:** keep letters only, lowercase, remove English stop words (NLTK), and reduce words to their stems (Porter stemmer).
3. **Features:** bag of words over the 1,500 most frequent terms (`CountVectorizer`).
4. **Model:** Multinomial Naive Bayes (alpha = 0.1), trained on an 80/20 train-test split. The training script prints the test accuracy.
5. **Web app:** `app.py` applies the same cleaning to the text a user types and shows the predicted label.

## Files

| File | Purpose |
|---|---|
| `Sentiment Analysis of Restaurant Reviews.py` | Cleans the data, trains the model, saves `Restaurant-reviews-model.pkl` and `corpus.pkl` |
| `app.py` | Flask app that serves predictions |
| `Restaurant_Reviews.tsv` | Labelled review dataset |
| `main.css`, `main.js` | Front-end styling and form validation |
| `requirements.txt` | Python dependencies |

## Run

```bash
pip install -r requirements.txt
python "Sentiment Analysis of Restaurant Reviews.py"   # trains the model and writes corpus.pkl
python app.py                                          # open http://127.0.0.1:5000
```
