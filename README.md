# 🛒 E-commerce Product Categorization with Machine Learning

## 📌 Project Overview

In modern e-commerce, large marketplaces need to **automatically assign product categories** based on the product description. Manual categorization is error-prone, time-consuming, and difficult to scale.

The goal of this project is to build a **text classification model** that predicts the category of an item from its description. I use classical Natural Language Processing (NLP) techniques (text cleaning, TF-IDF vectorization) and a baseline **Logistic Regression** classifier to demonstrate end-to-end categorization.

---

## 📊 Data Exploration

The dataset consists of product descriptions and their corresponding categories.

* **Number of samples:** ~50,425 products
* **Categories:** 4 main groups (Books, Clothing & Accessories, Electronics, Household)
* **Example rows:**

| Description                                         | Category               |
| --------------------------------------------------- | ---------------------- |
| Barron's TOEFL iBT 15th edition (DVD) This is ...   | Books                  |
| Vibhavari Men's Black Sleek Tie, Pocket Square...   | Clothing & Accessories |
| Tokina 11-16mm f/2.8 AT-X116 Pro DX II Digital...   | Electronics            |
| Camlin Arfina Artist'S Picture Varnish Spray C...   | Household              |

This dataset reflects typical real-world e-commerce text data: include specs, sometimes noisy, with inconsistent formatting.

---

## ⚙️ Methodology

### 1. Data Preprocessing

To prepare the raw text for modeling, I performed the following steps:

* **Lowercasing** → ensures uniform text (e.g., “Book” = “book”).
* **Regex cleaning** → removed special characters, punctuation.
* **Tokenization** → split sentences into words.
* **Stopword removal** → removed common but uninformative words (“and”, “the”, etc.).
* **Lemmatization** → reduced words to their base form (“phones” → “phone”).

### 2. Feature Engineering

* Converted text into numerical features using **TF-IDF (Term Frequency-Inverse Document Frequency)**.
* Limited vocabulary to **5,000 features** for efficiency.

### 3. Model

* Chose **Logistic Regression** as a **baseline classifier**:

  * Simple, interpretable, and performs well on linearly separable text classification tasks.
  * Provides a benchmark before exploring more advanced models (Naive Bayes, SVM, deep learning).

---

## 📈 Results

Evaluation on the test set (20% split):

* **Accuracy:** 94.3%
* **Classification Report:**

| Category               | Precision | Recall | F1-score |
| ---------------------- | --------- | ------ | -------- |
| Books                  | 0.95      | 0.94   | 0.95     |
| Clothing & Accessories | 0.96      | 0.96   | 0.96     |
| Electronics            | 0.95      | 0.91   | 0.93     |
| Household              | 0.93      | 0.96   | 0.94     |

* **Confusion Matrix** (true vs. predicted categories):

  * Most errors come from confusion between **Electronics** and **Household**, which often share overlapping vocabulary (e.g., “appliances”, “charger”).

---

## 📝 Conclusion

This project demonstrates that even a **baseline ML pipeline** with TF-IDF + Logistic Regression can achieve **94% accuracy** in categorizing products.

### 🔑 Key Learnings:

* Proper **text preprocessing** significantly improves classification.
* **TF-IDF** is a strong baseline for text features.
* Logistic Regression provides a solid starting point.

### 🚀 Future Improvements:

* Try other models like **Naive Bayes, SVM, or Random Forest**.
* Use **word embeddings** (Word2Vec, GloVe, fastText) or **transformer models** (BERT).
* Perform **hyperparameter tuning** for optimization.
* Expand dataset to include more categories and languages.

---

## 📂 Repository Contents

* `ecommerceDataset.csv` → Raw dataset
* `ProductCategorizer.ipynb` → Colab notebook
* `logistic_prodcatger_model.pkl` → Trained Logistic Regression model
* `tfidf_vectorizer.pkl` → Saved TF-IDF vectorizer
* `README.md` → This project report

---

## 👩🏽‍💻 Author

Developed by **[Mercy Okanlawon]**
Feel free to open issues or suggest improvements.
