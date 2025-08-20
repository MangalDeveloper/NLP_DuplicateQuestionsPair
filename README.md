# 🔍 NLP Duplicate Question Pairs Detection

This project tackles the **Quora Duplicate Questions Challenge** from Kaggle, where the goal is to identify whether two given questions are semantically similar (duplicates) or not.  

Using **Natural Language Processing (NLP)** techniques, advanced preprocessing, and feature engineering, the model is able to achieve **~80% accuracy** and is deployed on **Streamlit Community Cloud** for interactive use.

---

## 📌 Features
- Preprocessing pipeline with:
  - Text cleaning and normalization
  - Stopwords removal
  - Tokenization
- **Bag of Words (BoW)** representation with `cv.pkl`
- **Advanced Feature Engineering**:
  - Custom similarity measures
  - Fuzzy string matching (using `fuzzywuzzy`)
  - Hand-crafted distance-based features
- **Random Forest Classifier** trained for classification
- Deployment using **Streamlit** with `model.pkl`, `cv.pkl`, and `stopwords.pkl`

---

## ⚙️ Preprocessing & Feature Engineering  

### Preprocessing Steps
Before training, extensive preprocessing was performed to normalize and clean the text data:  
- **Text Cleaning**: Removal of special characters, punctuation, digits, and unnecessary whitespace.  
- **Lowercasing**: Standardized text by converting everything to lowercase.  
- **Stopwords Removal**: Custom stopword list stored in `stopwords.pkl` to eliminate non-informative words.  
- **Stemming/Lemmatization**: Reduced words to their root forms for consistency.  
- **Tokenization**: Split sentences into tokens for feature extraction.  

### Advanced Features Implemented
Beyond Bag of Words (BoW), additional handcrafted features were created to capture semantic similarity:  

1. **Basic Features**  
   - Length of question 1 and question 2  
   - Difference in lengths  
   - Number of common words between both questions  
   - Ratio of common words to total unique words  

2. **FuzzyWuzzy Similarity Scores**  
   Using the `fuzzywuzzy` package to compute:  
   - `fuzz.QRatio` – Quick ratio similarity  
   - `fuzz.partial_ratio` – Partial string match score  
   - `fuzz.token_sort_ratio` – Token-based matching ignoring word order  
   - `fuzz.token_set_ratio` – Token set overlap score  

3. **Distance-Based Features**  
   - Cosine distance between BoW representations  
   - Jaccard similarity of token sets  
   - Word overlap features  

4. **Composite Features**  
   - Weighted combinations of word matches and fuzzy scores  
   - Ratios such as `(common_words / min(len(q1), len(q2)))`  

These engineered features were concatenated with the **BoW vectors** (`cv.pkl`) and then used to train a **Random Forest Classifier**.  

✅ This combination of preprocessing and custom features helped push the model to **~80% accuracy**, improving significantly over plain BoW models.

---

## 🛠 Tech Stack
- Python 3.10
- NLTK, Scikit-learn, Bs4
- FuzzyWuzzy, Distance
- Streamlit
- Pickle for model persistence

---

🌐 Deployment

  ## 🚀 Live Demo
  Check out the live app on Streamlit Community Cloud here: [Streamlit App](https://nlpduplicatequestionspair-gql6pp2cngxgfkfuaxs9cj.streamlit.app/)

📊 Model Performance

  Model: Random Forest Classifier
  Accuracy: 80%
  Dataset: Quora Question Pairs

🙌 Acknowledgements

  [Kaggle: Quora Question Pairs Challenge](https://www.kaggle.com/c/quora-question-pairs)
  [Streamlit](https://streamlit.io/)  
  Open-source NLP libraries (NLTK, Scikit-learn, FuzzyWuzzy)

## 📸 App Screenshot

![Streamlit App Screenshot](./Screenshots/app_screenshot.png)
