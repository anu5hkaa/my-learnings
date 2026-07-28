# Hotel Booking Cancellation Prediction using Decision Tree

## Project Objective

The main objective of this project was not only to predict hotel booking cancellations but also to gain a practical understanding of how the Decision Tree algorithm works.

Throughout this project, I explored how a Decision Tree makes decisions, how different hyperparameters affect model performance, and how techniques such as pre-pruning and post-pruning help improve generalization by reducing overfitting. The goal was to understand the complete learning process of a Decision Tree rather than focusing only on achieving high accuracy.

---

# Understanding Decision Tree

A Decision Tree is a **supervised machine learning algorithm** that can be used for both **classification** and **regression** problems. In this project, it was used for a **classification task** to predict whether a hotel booking would be cancelled.

A Decision Tree works like a sequence of **if-else conditions**. It starts from a **root node**, repeatedly splits the data based on the best feature, creates internal decision nodes, and finally reaches **leaf nodes** that contain the final prediction. The objective is to create groups that are as pure as possible, meaning that most records in a leaf belong to the same class.

Unlike many machine learning algorithms, a Decision Tree:

- Does not require feature scaling or normalization.
- Can handle both numerical and categorical features.
- Captures non-linear relationships between variables.
- Is relatively robust to outliers.
- Is easy to understand and interpret because its decisions can be visualized.

---

# How a Decision Tree Chooses the Best Split

One of the most important concepts I learned is **node impurity**.

Initially, the data contains a mixture of different classes. The goal of every split is to reduce this impurity and create purer child nodes.

To measure impurity, Decision Trees commonly use:

- **Gini Index**
- **Entropy**

After evaluating all possible splits, the algorithm selects the split that provides the highest **Information Gain**, which means the impurity decreases the most after the split.

In simple terms:

- Lower Gini or Entropy = More Pure Node
- Higher Information Gain = Better Split

For this project, **Gini Index** produced slightly better performance than Entropy and was therefore selected.

---

# Overfitting and Pruning

One limitation of Decision Trees is **overfitting**.

If the tree keeps splitting until every training example is perfectly classified, it starts memorizing the training data instead of learning general patterns. As a result, the training accuracy becomes very high, but the testing performance may decrease.

To overcome this problem, I explored two pruning techniques.

### Pre-Pruning

Pre-pruning stops the tree from growing beyond a certain complexity by defining hyperparameters before training begins.

The main hyperparameters I experimented with were:

- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `criterion`

Different combinations were tested to achieve the best balance between training and testing performance.

---

### Post-Pruning

In post-pruning, the Decision Tree is first grown completely and then unnecessary branches are removed using **Cost Complexity Pruning (`ccp_alpha`)**.

Removing less important branches simplifies the model, reduces overfitting, and improves generalization on unseen data.

---

# Hyperparameter Selection

After several experiments, the following hyperparameters produced the best overall performance.

### Final Pre-Pruned Model

```python
DecisionTreeClassifier(
    criterion="gini",
    max_depth=10,
    min_samples_split=5,
    min_samples_leaf=10,
    random_state=42
)
```

### Final Post-Pruned Model

```python
DecisionTreeClassifier(
    criterion="gini",
    max_depth=10,
    min_samples_split=5,
    min_samples_leaf=10,
    ccp_alpha=0.0001,
    random_state=42
)
```

Although the improvement was small, the post-pruned model consistently achieved slightly better testing performance and therefore was selected as the final model.

---

# Final Model Performance

| Metric | Training | Testing |
|---------|---------:|--------:|
| Accuracy | 82.47% | **81.59%** |
| Precision | 70.21% | **68.15%** |
| Recall | 62.92% | **62.00%** |
| F1 Score | 66.37% | **64.93%** |

The small difference between training and testing performance indicates that the model generalizes well and does not suffer from significant overfitting.

---

# Business Insights

Some meaningful insights obtained from the dataset include:

### 1. Longer Lead Time Increases Cancellation Probability

Customers who booked much earlier were more likely to cancel their reservations.

- Average Lead Time (Cancelled): **105.72 days**
- Average Lead Time (Not Cancelled): **70.11 days**

This suggests that customers who book several months in advance are more likely to change their travel plans.

---

### 2. Customers Making More Special Requests Rarely Cancel

Guests who completed their stay generally made more special requests than customers who cancelled.

This indicates that customers investing more effort in personalizing their stay are usually more committed to their bookings.

---

### 3. Country Influences Cancellation Behaviour

Country was one of the most important features in the Decision Tree.

Different countries showed different cancellation patterns, indicating that customer behaviour varies across regions.

---

### 4. Online Travel Agency Bookings Have Higher Cancellation Risk

Bookings made through Online Travel Agencies were among the strongest predictors of cancellation, suggesting that OTA customers generally have greater flexibility to cancel or modify reservations.

---

# What I Learned

Through this project, I developed a much deeper understanding of Decision Trees beyond simply training a model.

I learned:

- How a Decision Tree makes decisions using recursive splitting.
- The importance of node impurity and Information Gain.
- The difference between Gini Index and Entropy.
- How hyperparameters influence model complexity.
- How to detect overfitting using training and testing metrics.
- How Pre-Pruning and Post-Pruning improve model generalization.
- How to interpret feature importance to generate meaningful business insights.
- How evaluation metrics such as Accuracy, Precision, Recall, and F1-Score help assess model performance instead of relying only on accuracy.

I also understood why Decision Trees are rarely used alone for large and complex datasets. Since a single tree can become unstable and overfit easily, ensemble methods such as **Random Forest**, **Bagging**, and **Boosting** combine multiple Decision Trees to produce more accurate, stable, and robust predictions.

Overall, this project helped me understand both the theoretical concepts and the practical implementation of Decision Trees in a real-world machine learning problem.
