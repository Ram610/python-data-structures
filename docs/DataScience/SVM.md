
# Support Vector Machines (SVM) in Python

Support Vector Machines (SVM) are powerful supervised learning algorithms used for classification and regression. SVMs find the optimal hyperplane that separates data points of different classes with the maximum margin.

---

## Real-Life Applications
- Face detection in images
- Text classification (spam vs. not spam)
- Handwriting recognition
- Bioinformatics (classifying proteins)

---

## What is an SVM?

- **Classification:** SVM finds the best boundary (hyperplane) that separates classes.
- **Regression:** SVM can also be used for regression (SVR).
- **Kernel Trick:** SVMs can use kernels (linear, polynomial, RBF) to handle non-linear data.

---

## Example: SVM Classifier with scikit-learn

```python
from sklearn.datasets import load_iris
from sklearn.svm import SVC
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load data
data = load_iris()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model (RBF kernel)
svm = SVC(kernel='rbf', C=1.0, gamma='scale')
svm.fit(X_train, y_train)

# Predict
y_pred = svm.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

## Example: SVM Regression (SVR)

```python
from sklearn.svm import SVR
import numpy as np
import matplotlib.pyplot as plt

# Generate data
X = np.linspace(0, 10, 100).reshape(-1, 1)
y = np.sin(X).ravel() + np.random.randn(100) * 0.1

# Model
svr = SVR(kernel='rbf', C=100, gamma=0.1, epsilon=0.1)
svr.fit(X, y)

y_pred = svr.predict(X)

plt.scatter(X, y, color='blue', label='Actual')
plt.plot(X, y_pred, color='red', label='Predicted')
plt.legend()
plt.title('SVM Regression')
plt.show()
```

---


---

## Multiple Choice Questions

1. What does SVM try to maximize?
	a) Number of clusters
	b) Margin between classes
	c) Number of features
	d) Training time

2. What is the kernel trick used for in SVM?
	a) To speed up training
	b) To handle non-linear data
	c) To reduce dimensionality
	d) To increase overfitting

3. Which of the following is NOT a real-life application of SVM?
	a) Face detection
	b) Text classification
	c) Predicting house prices
	d) Handwriting recognition

4. What is a drawback of SVM for large datasets?
	a) Too fast
	b) Slow training and prediction
	c) Cannot handle text data
	d) Only works for regression

---

## Reflective Questions
- How would you use SVM for text classification?
- What features might be important for face detection?
- Can you think of a scenario where SVM would not be the best choice?

---

## Practice Exercise

**Task:**
- Use the breast cancer dataset from scikit-learn.
- Train an SVM classifier and print the accuracy on the test set.

**Starter code:**
```python
from sklearn.datasets import load_breast_cancer
from sklearn.svm import SVC
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load data
data = load_breast_cancer()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
svm = SVC(kernel='linear')
svm.fit(X_train, y_train)

# Predict
y_pred = svm.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

## Key Points
- SVMs are effective for high-dimensional data.
- The kernel trick allows SVMs to handle non-linear data.
- SVMs can be slow for large datasets.

---

## Further Reading
- [scikit-learn SVC documentation](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html)
- [SVM Tutorial](https://www.datacamp.com/tutorial/svm-classification-scikit-learn-python)
