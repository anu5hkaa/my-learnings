# Understanding Naive Bayes using SMS Text Classification

## Project Overview

This project was created to understand the **Multinomial Naive Bayes** algorithm by implementing it on a real-world SMS text classification dataset.

Rather than focusing only on spam detection, the primary objective was to study:

* How Naive Bayes works mathematically
* The assumptions behind the algorithm
* How text is converted into numerical features using TF-IDF
* How class probabilities are calculated
* The effect of class imbalance and the use of SMOTE
* The strengths and limitations of Naive Bayes

The SMS dataset serves as a practical example to understand the complete workflow of Naive Bayes for text classification.

---

# Objective

The objective of this project is to gain a practical understanding of the **Multinomial Naive Bayes** algorithm by implementing it on a text classification task and analyzing its performance, assumptions, advantages, and limitations.

---

# Dataset

**SMS Spam Collection Dataset**

* Total Messages: 5,572
* Classes:

  * Ham
  * Spam

---

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Imbalanced-learn (SMOTE)
* Google Colab

---

# Implementation Pipeline

1. Load Dataset
2. Remove Duplicate Records
3. Encode Target Labels
4. Split Dataset into Train and Test Sets
5. Convert Text into TF-IDF Features
6. Apply SMOTE on the Training Data
7. Train the Multinomial Naive Bayes Model
8. Evaluate Model Performance
9. Analyze the strengths and limitations of Naive Bayes

---

# Naive Bayes Formula

Naive Bayes predicts the class using Bayes' Theorem:

[
P(C|X)=\frac{P(X|C)\times P(C)}{P(X)}
]

Where:

* **P(C|X)** – Posterior Probability
* **P(X|C)** – Likelihood
* **P(C)** – Prior Probability
* **P(X)** – Evidence

The classifier predicts the class with the highest posterior probability.

---

# Model Evaluation

| Metric    |  Value |
| --------- | -----: |
| Accuracy  | 97.48% |
| Precision |   0.87 |
| Recall    |   0.95 |
| F1-Score  |   0.91 |

---

# Key Learnings

During this project, I learned that:

* Multinomial Naive Bayes is widely used for text classification problems.
* It assumes that all input features are conditionally independent.
* It performs well on high-dimensional datasets with a large number of features.
* It works particularly well with TF-IDF and Bag-of-Words representations.
* Since Naive Bayes is a probability-based algorithm, feature scaling is not required.
* The algorithm is generally robust to outliers because predictions depend on probabilities rather than distances.
* It is computationally efficient and serves as an excellent baseline model.
* It is commonly used for:

  * Spam Detection
  * Sentiment Analysis
  * Twitter Sentiment Analysis
  * Document Classification
  * Email Filtering
  * News Categorization

---

# Assumptions

The primary assumption of Naive Bayes is:

> All input features are conditionally independent given the class.

Although this assumption is rarely true in real-world datasets, Naive Bayes often performs surprisingly well for text classification tasks.

---

# Laplace Smoothing

A common issue in Naive Bayes is the **Zero Probability Problem**.

If a word never appears in a particular class during training, its probability becomes zero, making the overall prediction probability zero.

To overcome this issue, **Laplace Smoothing (Add-One Smoothing)** is applied:

[
P=\frac{Count+\alpha}{Total+\alpha\times Vocabulary}
]

where:

* α = 1 (commonly used)

This ensures that every word receives a small non-zero probability.

---

# Advantages

* Very fast to train and predict
* Works well with large feature spaces
* Excellent baseline model
* Requires relatively little training data
* No feature scaling required
* Memory efficient
* Performs well on text classification tasks
* Robust to outliers

---

# Limitations

* Assumes feature independence
* Cannot capture relationships between features
* High Bias and Low Variance algorithm
* Struggles when features are highly correlated (collinearity)
* Cannot learn complex patterns
* Ignores word order, making it less effective for tasks where sequence is important
* Modern Transformer-based and LLM-based models generally outperform Naive Bayes on complex NLP tasks

---

# Conclusion

This project helped me understand the complete working of the **Multinomial Naive Bayes** algorithm through practical implementation.

I explored its mathematical foundation, probability-based predictions, assumptions, Laplace smoothing, evaluation metrics, advantages, and limitations. Although Naive Bayes is a simple algorithm, it remains an effective baseline for many traditional NLP tasks such as spam detection, sentiment analysis, and document classification.

---

# Author

**Anushka Thakur**

B.Tech in Artificial Intelligence & Data Science

Machine Learning | NLP | Data Science
