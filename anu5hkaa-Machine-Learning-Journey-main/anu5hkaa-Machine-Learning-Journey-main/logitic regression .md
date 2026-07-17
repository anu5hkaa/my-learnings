# Machine Learning Notes – My Understanding 

## Logistic Regression

Despite its name, Logistic Regression is **not a regression algorithm**. It is a **classification algorithm**.

It is mainly used for:

* Binary Classification
* Multiclass Classification
* Ordinal Classification (with suitable extensions)

---

## Why don't we use Linear Regression?

Initially, I thought, why can't we simply use Linear Regression for classification?

The problem is that Linear Regression predicts continuous values.

For classification, we need probabilities between **0 and 1**.

Linear Regression can predict values like:

* -2
* 1.5
* 8

which are impossible as probabilities.

Another issue is that if there is an outlier, the best-fit line shifts significantly, changing the prediction boundary.

So instead of Linear Regression, we use Logistic Regression.

---

## Sigmoid Function

Logistic Regression first calculates a linear equation.

Instead of directly giving that answer, it passes it through a **Sigmoid Function**.

The job of the Sigmoid Function is simply:

> Take any value and convert it into a probability between 0 and 1.

Now the model predicts probabilities instead of raw values.

For example:

* 0.92 means the model is 92% confident.
* 0.18 means the model is 18% confident.

After this, we apply a threshold (usually 0.5) to decide the final class.

---

## Cost Function (Log Loss)

After predicting the probability, the model asks itself:

> "How wrong am I?"

This is the purpose of the Cost Function.

Logistic Regression uses **Log Loss**.

Linear Regression uses **Mean Squared Error (MSE)**.

Why doesn't Logistic Regression use MSE?

Because Logistic Regression predicts probabilities using the Sigmoid Function.

MSE with Sigmoid creates optimization problems, making Gradient Descent much less effective.

Log Loss is specifically designed for classification.

It gives:

* Small loss for confident correct predictions.
* Large loss for confident wrong predictions.

The Cost Function itself does not improve the model.

It simply measures how wrong the prediction is.

---

## Gradient Descent

Once Log Loss measures the error,

Gradient Descent says:

> "Okay, I'll reduce this error."

So the learning process becomes:

Prediction

↓

Log Loss measures the error

↓

Gradient Descent updates the weights

↓

Better prediction

↓

Repeat

The model keeps repeating this until the cost becomes as small as possible.

---

## Decision Boundary

Although Logistic Regression uses a curved Sigmoid Function,

its **decision boundary is still linear**.

This confused me initially.

The Sigmoid only converts the output into probabilities.

The actual separation between the classes is still made using a linear equation.

This is also why Logistic Regression struggles when the data has highly complex patterns.

For those cases, we use models like:

* Decision Tree
* Random Forest
* XGBoost
* SVM with kernels

because they can learn non-linear decision boundaries.

---

# Assumptions of Logistic Regression

Assumptions are simply the things that the model expects from the data.

They are not rules.

They are conditions under which the model performs best.

### 1. Linear Decision Boundary

The model expects that the classes can be reasonably separated using a straight line.

If the classes are highly mixed together,

Logistic Regression may not perform well.

---

### 2. No Multicollinearity

The model expects that features should not provide the same information.

For example,

Height in centimeters

and

Height in meters

are almost identical.

Keeping both only increases complexity without adding new information.

---

### 3. Independent Observations

The model expects every row to be independent.

One observation should not simply be a copy of another.

Every training example should provide new information.

---

### 4. Limited Outliers

The model assumes there are no extreme outliers dominating the dataset.

Very large outliers can influence the learned coefficients and reduce performance.

---

# Overfitting

Initially, I thought overfitting simply meant learning the training data well.

But the better definition is:

> Overfitting means the model memorizes the training data, including noise, instead of learning the general pattern.

Such a model performs very well on training data,

but poorly on unseen data.

---

# Regularization

Sometimes the model becomes too dependent on one or a few features.

Those features receive very large weights.

This increases the chance of overfitting.

Regularization helps solve this.

Initially, I was confused by the word **penalty**.

Penalty doesn't directly change the weights.

Instead,

it adds an extra cost whenever the weights become too large.

Now the total cost becomes:

**Total Cost = Log Loss + Regularization Penalty**

Gradient Descent always tries to minimize the total cost.

So if the penalty increases because the weights are too large,

Gradient Descent naturally reduces those weights.

So I think of it like this:

* Log Loss says:

  > "Your prediction is wrong."

* Regularization says:

  > "Your weights are becoming too large."

* Gradient Descent says:

  > "I'll reduce both."

As a result,

the model becomes more generalized and less likely to memorize the training data.

---

# L1 Regularization (Lasso)

L1 asks one question:

> "Is this feature actually useful?"

If the answer is no,

it makes that feature's weight exactly **0**.

A weight of 0 means the feature no longer contributes to the prediction.

So L1 automatically removes unnecessary features.

That is why L1 performs **Feature Selection**.

I would use L1 when I believe many features are irrelevant.

---

# L2 Regularization (Ridge)

L2 has a different philosophy.

Instead of removing features,

it says:

> "Every feature may contribute something."

So instead of making weights zero,

it simply reduces them.

The feature remains in the model,

but its influence becomes smaller.

This is why L2 is used more often in practice.

Most real-world datasets have features that contribute at least a little,

so instead of removing them,

we simply reduce their importance.

---
