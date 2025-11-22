# K-Nearest Neighbors (KNN) in Python

K-Nearest Neighbors (KNN) is a simple, non-parametric, and instance-based learning algorithm used for classification and regression. It predicts the label of a new data point based on the majority label of its k closest neighbors in the feature space.

---

## What is KNN?

 **Classification:** Assigns the class most common among the k nearest neighbors.
 **Regression:** Predicts the average value of the k nearest neighbors.

KNN does not learn a model during training; it stores the entire dataset and makes predictions at query time.

---

## Example: KNN Classifier with scikit-learn

```python
from sklearn.datasets import load_iris
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load data
data = load_iris()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

# Predict
y_pred = knn.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

## Example: KNN Regression

```python
from sklearn.neighbors import KNeighborsRegressor
import numpy as np
import matplotlib.pyplot as plt

# Generate data
X = np.linspace(0, 10, 100).reshape(-1, 1)
y = np.sin(X).ravel() + np.random.randn(100) * 0.1

# Model
knn_reg = KNeighborsRegressor(n_neighbors=5)
knn_reg.fit(X, y)

y_pred = knn_reg.predict(X)

plt.scatter(X, y, color='blue', label='Actual')
plt.plot(X, y_pred, color='red', label='Predicted')
plt.legend()
plt.title('KNN Regression')
plt.show()
```

---

## Choosing k
- Small k: sensitive to noise, may overfit
- Large k: smoother decision boundary, may underfit
- Common to use odd k to avoid ties in classification

---

## Practice Exercise

**Task:**
- Use the digits dataset from scikit-learn.
- Train a KNN classifier and print the accuracy on the test set.

**Starter code:**
```python
from sklearn.datasets import load_digits
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load data
- Recommender systems (suggesting products based on similar users)
- Handwriting recognition (digit classification)
- Anomaly detection
- Predicting a person's political affiliation based on neighbors

---

## Multiple Choice Questions

1. What does KNN use to make predictions?
	a) Decision boundaries
	b) Nearest neighbors in feature space
	c) Regression lines
	d) Random guessing

2. What is a drawback of KNN for large datasets?
	a) Too fast
	b) Requires training phase
	c) Slow predictions
	d) Cannot handle categorical data

3. Which of the following is NOT a real-life application of KNN?
	a) Recommender systems
	b) Handwriting recognition
	c) Predicting house prices
	d) Anomaly detection

4. What is important to do before using KNN?
	a) Normalize or scale features
	b) Remove all categorical data
	c) Use only one feature
	d) Always set k=1

---

## Reflective Questions
- How would you use KNN to recommend movies to a user?
- What features might be important for handwriting recognition?
- Can you think of a scenario where KNN would not work well?

---
data = load_digits()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)

# Predict
y_pred = knn.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

## Key Points
- KNN is simple and effective for small datasets.
- No training phase; prediction can be slow for large datasets.
- Sensitive to feature scaling (normalize data for best results).

---

## Further Reading
- [scikit-learn KNeighborsClassifier documentation](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)
- [KNN Tutorial](https://www.datacamp.com/tutorial/k-nearest-neighbor-classification-scikit-learn)
