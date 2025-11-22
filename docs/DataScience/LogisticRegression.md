
# Logistic Regression in Python

Logistic regression is a classification algorithm used to predict the probability of a binary outcome (yes/no, 0/1, true/false) based on one or more input features. It is widely used for problems like spam detection, disease prediction, and more.

---

## Real-Life Applications
- Email spam detection (spam or not)
- Disease diagnosis (sick or healthy)
- Customer churn prediction (will leave or stay)
- Credit card fraud detection

---

## What is Logistic Regression?

Unlike linear regression, logistic regression predicts the probability that a given input belongs to a particular class using the logistic (sigmoid) function:

$$
P(y=1|x) = \frac{1}{1 + e^{-(mx + c)}}
$$

Where:
- $P(y=1|x)$ = probability of class 1
- $x$ = input feature
- $m$ = coefficient (weight)
- $c$ = intercept (bias)

---

## Example: Logistic Regression with scikit-learn

```python
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report

# Load data (binary classification: setosa vs not-setosa)
data = load_iris()
X = data.data[data.target != 2]
y = data.target[data.target != 2]

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
model = LogisticRegression()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
print(classification_report(y_test, y_pred))
```

---

## Visualizing the Sigmoid Function

```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(z):
    return 1 / (1 + np.exp(-z))

z = np.linspace(-10, 10, 100)
plt.plot(z, sigmoid(z))
plt.title('Sigmoid Function')
plt.xlabel('z')
plt.ylabel('sigmoid(z)')
plt.grid(True)
plt.show()
```

---


---

## Multiple Choice Questions

1. What type of problem does logistic regression solve?
    a) Regression
    b) Clustering
    c) Classification
    d) Dimensionality reduction

2. What is the output of the sigmoid function?
    a) Any real number
    b) Probability between 0 and 1
    c) Only 0 or 1
    d) A cluster label

3. Which of the following is NOT a real-life application of logistic regression?
    a) Spam detection
    b) Predicting house prices
    c) Disease diagnosis
    d) Fraud detection

4. What metric is commonly used to evaluate logistic regression?
    a) Mean Squared Error
    b) Accuracy
    c) Inertia
    d) Silhouette Score

---

## Reflective Questions
- How would you use logistic regression to predict if a customer will buy a product?
- What features might be important for predicting credit card fraud?
- Can you think of a scenario where logistic regression would not be suitable?

---

## Practice Exercise

**Task:**
- Use the breast cancer dataset from scikit-learn.
- Train a logistic regression model to classify malignant vs benign tumors.
- Print the accuracy and confusion matrix.

**Starter code:**
```python
from sklearn.datasets import load_breast_cancer
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, confusion_matrix

# Load data
data = load_breast_cancer()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model
model = LogisticRegression(max_iter=10000)
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
```

---

## Key Points
- Logistic regression is used for binary classification.
- The output is a probability between 0 and 1.
- Use metrics like accuracy, precision, recall, and confusion matrix to evaluate.

---

## Further Reading
- [scikit-learn LogisticRegression documentation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html)
- [Logistic Regression Tutorial](https://www.datacamp.com/tutorial/logistic-regression-python)
