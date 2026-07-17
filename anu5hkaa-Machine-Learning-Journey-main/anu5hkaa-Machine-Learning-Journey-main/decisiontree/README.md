# My Understanding of Decision Trees

While learning Decision Trees, I understood that the main goal of the algorithm is to learn patterns from training data and use those patterns to make predictions on unseen data.

A Decision Tree starts by calculating the entropy of the current node. Entropy measures how pure or impure the data is. If the entropy is 0, the node is completely pure and no further splitting is required. However, if the node is impure, the tree needs to find the best way to split the data.

To determine the best split, the tree calculates Information Gain for each available feature. Information Gain measures how much uncertainty is reduced after splitting on a particular feature. The feature with the highest Information Gain is selected because it provides the most useful information about the target variable.

After selecting the best feature, the node is split into child nodes. The same process is repeated recursively on each impure child node. For every new node, entropy is calculated, Information Gain is computed for the remaining features, and the best split is chosen again.

I also learned that the purpose of entropy is not to make predictions directly. Entropy only tells us how mixed the data is. Information Gain helps us decide which feature should be used for splitting. Together, they allow the Decision Tree to discover useful rules hidden in the data.

One important insight I gained is that pure leaf nodes are not the final objective. The real objective is to create a model that generalizes well to unseen data. If a tree keeps splitting until it memorizes the training data, it can suffer from overfitting.

To prevent overfitting, pruning techniques are used. In pre-pruning, restrictions such as maximum depth, minimum samples per split, or minimum samples per leaf are applied before the tree grows too large. In post-pruning, the tree is first grown completely and then unnecessary branches are removed if they do not improve performance.

I also learned the difference between Decision Tree Classification and Decision Tree Regression. In classification problems, the tree uses entropy or Gini impurity to evaluate splits and predicts categorical outputs such as Yes/No or Placed/Not Placed. In regression problems, the target variable is continuous, such as salary, house price, or temperature. Since there are no classes, entropy is not used. Instead, the tree uses variance reduction or mean squared error reduction to find the best split. The goal is to create groups where the target values are as similar as possible.

Overall, my understanding is that Decision Trees work by repeatedly asking the most informative questions, reducing uncertainty at each step, and gradually learning decision rules that can be used to predict outcomes for new data points.
