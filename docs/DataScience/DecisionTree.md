
# Decision Trees in Python

Decision trees are supervised learning algorithms used for both classification and regression tasks. They work by splitting the data into branches based on feature values, leading to a tree-like structure of decisions.

---

## Real-Life Applications
- Medical diagnosis (e.g., is a tumor benign or malignant?)
- Loan approval (approve or reject)
- Customer segmentation
- Predicting whether a customer will default on a loan

---

## What is a Decision Tree?

A decision tree splits data into subsets based on the value of input features. Each node represents a feature, each branch a decision rule, and each leaf a final outcome (class or value).

---

## Example: Decision Tree Classifier with scikit-learn

```python
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier, plot_tree
import matplotlib.pyplot as plt

# Load data
data = load_iris()
X = data.data
y = data.target

# Model
model = DecisionTreeClassifier(max_depth=3, random_state=42)
model.fit(X, y)

# Visualize tree
plt.figure(figsize=(12,8))
plot_tree(model, feature_names=data.feature_names, class_names=data.target_names, filled=True)
plt.title('Decision Tree for Iris Dataset')
plt.show()
```

---

## Example: Decision Tree Regressor

```python
from sklearn.tree import DecisionTreeRegressor
import numpy as np
import matplotlib.pyplot as plt

# Generate data
X = np.linspace(0, 10, 100).reshape(-1, 1)
y = np.sin(X).ravel() + np.random.randn(100) * 0.1

# Model
reg = DecisionTreeRegressor(max_depth=3)
reg.fit(X, y)

y_pred = reg.predict(X)

plt.scatter(X, y, color='blue', label='Actual')
plt.plot(X, y_pred, color='red', label='Predicted')
plt.legend()
plt.title('Decision Tree Regression')
plt.show()
```

---


---

## Multiple Choice Questions

1. What is the main advantage of decision trees?
	a) They are always the most accurate
	b) They are easy to interpret and visualize
	c) They require a lot of data preprocessing
	d) They cannot handle categorical data

2. What is a leaf node in a decision tree?
	a) A node that splits data
	b) The root node
	c) A node with no children (final decision)
	d) A node with only one child

3. Which of the following is NOT a real-life application of decision trees?
	a) Medical diagnosis
	b) Image compression
	c) Loan approval
	d) Customer segmentation

4. What is a common problem with decision trees?
	a) Underfitting
	b) Overfitting
	c) Cannot handle numerical data
	d) Too fast

---

## Reflective Questions
- How would you use a decision tree to decide whether to approve a loan?
- What features might be important for a medical diagnosis decision tree?
- Can you think of a scenario where a decision tree would not be the best choice?

---

## Practice Exercise

**Task:**
- Use the wine dataset from scikit-learn.
- Train a decision tree classifier and print the accuracy on the test set.

**Starter code:**
```python
from sklearn.datasets import load_wine
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load data
data = load_wine()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
model = DecisionTreeClassifier(max_depth=4)
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

## Key Points
- Decision trees are easy to interpret and visualize.
- They can handle both categorical and numerical data.
- Prone to overfitting; use pruning or set max_depth.

---

## Further Reading
- [scikit-learn DecisionTreeClassifier documentation](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)
- [Decision Trees Tutorial](https://www.datacamp.com/tutorial/decision-tree-classification-python)
