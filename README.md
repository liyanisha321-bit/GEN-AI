# GEN-AI

#  AI-Driven Sentiment Analysis for Stock Market News

## Overview

This project uses **Generative AI, Natural Language Processing (NLP), Machine Learning, and Deep Learning** techniques to analyze financial news and identify its sentiment.

The system processes financial news articles, converts the text into numerical embeddings using different **text embedding techniques**, and then uses machine learning and neural network models to classify the sentiment as **Positive, Neutral, or Negative**.

The project aims to provide useful insights that can support financial analysts and investors in understanding market sentiment and making more informed investment decisions.

---

##  Objective

The main objective of this project is to develop an AI-driven sentiment analysis system that can predict the sentiment of financial news.

### Key Objectives

* Analyze financial news articles using NLP techniques.
* Convert textual data into numerical representations using embeddings.
* Generate embeddings using **Word2Vec** and **Sentence Transformers**.
* Build Random Forest and Neural Network classification models.
* Compare the performance of different embedding-model combinations.
* Evaluate models using Accuracy, Precision, Recall, and F1-score.
* Select the best-performing model for sentiment prediction.
* Generate sentiment predictions for new financial news.

---

##  Business Context

Stock prices can be influenced by financial performance, innovations, collaborations, economic conditions, and market sentiment.

The large volume of financial news makes it difficult for investors and analysts to manually analyze every article and understand its potential market impact.

This project addresses this challenge by developing an automated AI-based sentiment analysis system that processes financial news and provides sentiment-based insights. These insights can help financial analysts incorporate news sentiment into investment strategies.

---

##  Problem Statement

An investment startup has historical daily financial news along with stock price and trading-volume information for a company listed on NASDAQ.

The goal is to develop an AI-driven system that can automatically analyze stock-related news, identify its sentiment, and provide useful insights for financial analysts and investment decision-making.

---

##  Dataset Description

The dataset contains **349 records and 8 columns**. The data covers financial news and stock information from January 2019 to April 2019.

### Dataset Features

| Feature  | Description                         |
| -------- | ----------------------------------- |
| `Date`   | Date on which the news was released |
| `News`   | Financial news article content      |
| `Open`   | Opening stock price                 |
| `High`   | Highest stock price during the day  |
| `Low`    | Lowest stock price during the day   |
| `Close`  | Adjusted closing stock price        |
| `Volume` | Number of shares traded             |
| `Label`  | Sentiment polarity                  |

### Sentiment Labels

* **1 → Positive**
* **0 → Neutral**
* **-1 → Negative**

---

##  Data Preprocessing & Exploration

The dataset was explored before model development.

The following steps were performed:

* Checked the first and last records.
* Checked dataset shape.
* Checked missing values.
* Checked duplicate values.
* Analyzed sentiment distribution.
* Examined numerical-variable distributions.
* Analyzed news-content length.
* Performed month-wise analysis.
* Studied correlations between variables.
* Analyzed sentiment against stock price.
* Performed time-series analysis.
* Compared news length across sentiment categories.

The dataset contains **349 rows and 8 columns**, and the notebook shows **no missing values** across the available columns.

---

##  Text Embedding Techniques

To enable machine learning models to understand textual information, the financial news was converted into numerical vectors.

### 1. Word2Vec

Word2Vec was used to generate word-level embeddings and represent the textual information numerically.

### 2. Sentence Transformers

Sentence Transformer models were used to generate contextual sentence-level embeddings.

The project experimented with:

* `BAAI/bge-base-en-v1.5`
* `all-MiniLM-L6-v2`

These embeddings capture semantic information from financial news and can be used as input to classification models.

---

## 🤖 Machine Learning Models

Two major types of classification models were developed.

### Random Forest

Random Forest models were built using:

* Word2Vec embeddings
* Sentence Transformer – BAAI embeddings
* Sentence Transformer – all-MiniLM-L6-v2 embeddings

### Neural Network

Neural Network models were built using:

* Word2Vec embeddings
* Sentence Transformer – BAAI embeddings
* Sentence Transformer – all-MiniLM-L6-v2 embeddings

The models were trained using an **80:20 training-testing split** with `random_state=42`.

---

## 📏 Model Evaluation

The models were evaluated using:

* **Accuracy**
* **Precision**
* **Recall**
* **F1-score**
* **Confusion Matrix**

These metrics were used to compare the generalization performance of different models on unseen test data.

---

## 🏆 Model Performance

| Model                                 |   Accuracy |  Precision |     Recall |   F1-Score |
| ------------------------------------- | ---------: | ---------: | ---------: | ---------: |
| Word2Vec + Random Forest              |     41.43% |     32.89% |     41.43% |     32.57% |
| Word2Vec + Neural Network             |     44.29% |     19.61% |     44.29% |     27.19% |
| BAAI + Random Forest                  |     41.43% |     32.89% |     41.43% |     32.57% |
| BAAI + Neural Network                 |     44.29% |     19.61% |     44.29% |     27.19% |
| all-MiniLM-L6-v2 + Random Forest      |     48.57% |     58.04% |     48.57% |     40.89% |
| **all-MiniLM-L6-v2 + Neural Network** | **54.29%** | **55.84%** | **54.29%** | **53.97%** |

Based on the test-set comparison in the notebook, **Sentence Transformer `all-MiniLM-L6-v2` + Neural Network** achieved the highest overall performance, with **54.29% accuracy and 53.97% F1-score**.

---

## ⭐ Best Model

### Sentence Transformer – all-MiniLM-L6-v2 + Neural Network

The final selected model uses:

**Financial News → Sentence Transformer Embedding → Neural Network → Sentiment Prediction**

The model achieved:

* **Accuracy:** 54.29%
* **Precision:** 55.84%
* **Recall:** 54.29%
* **F1-score:** 53.97%

This model was selected based on its comparatively stronger test-set performance.

---

##  Prediction

The selected model was also used to generate sentiment predictions for new financial news articles.

The output contains a `Predicted_Sentiment` column representing the predicted sentiment class:

* `1` → Positive
* `0` → Neutral
* `-1` → Negative

This allows the trained model to be applied to previously unseen financial news.

---

##  Key Observations

* Financial news can contain useful information related to market sentiment.
* Text embeddings transform unstructured news into numerical features suitable for machine learning.
* Word2Vec models provided relatively limited test performance in this dataset.
* Sentence Transformer embeddings provided richer contextual representations.
* The `all-MiniLM-L6-v2` based models performed better than the other tested approaches.
* The `all-MiniLM-L6-v2 + Neural Network` combination achieved the best test performance among the evaluated models.
* The relatively modest test accuracy indicates that further improvement is required before real-world financial deployment.

---

##  Recommendations & Future Improvements

The project recommends several ways to improve the system:

1. Use a larger and more diverse financial-news dataset.
2. Experiment with advanced financial language models such as **BERT or FinBERT**.
3. Try additional machine learning and deep learning algorithms.
4. Perform hyperparameter tuning and cross-validation.
5. Include additional financial indicators such as stock prices, trading volume, and market trends.
6. Continuously update the model with recent financial news.
7. Evaluate the system using multiple performance metrics.
8. Develop a real-time prediction system to assist investors.

---

##  Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Gensim
* Word2Vec
* Sentence Transformers
* Transformers
* TensorFlow
* Keras
* PyTorch

The notebook specifically imports libraries for data manipulation, visualization, embeddings, model training, and evaluation.





## 🏁 Conclusion

This project demonstrates how **Generative AI, NLP, text embeddings, and machine learning** can be combined to analyze financial news sentiment.

Different embedding techniques and classification models were compared systematically. Among the tested approaches, the **Sentence Transformer `all-MiniLM-L6-v2` with a Neural Network** produced the strongest test-set performance.

The project provides a foundation for developing an automated financial-news sentiment analysis system. With a larger dataset, advanced financial language models, additional market indicators, and further model optimization, the system can be improved for more reliable real-world applications.
