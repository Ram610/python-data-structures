
# Linear Regression in Python

Linear regression is a fundamental machine learning algorithm used to model the relationship between a dependent variable (target) and one or more independent variables (features). It is widely used for predictive analysis and trend forecasting.

---

## What is Linear Regression?

Linear regression fits a straight line (in 2D) or a hyperplane (in higher dimensions) to the data, minimizing the distance between the actual data points and the predicted values.

**Equation of a simple linear regression:**

$$
y = mx + c
$$

Where:
- $y$ = predicted value (dependent variable)
- $x$ = input feature (independent variable)
- $m$ = slope (coefficient)
- $c$ = intercept

---

## Real-Life Applications
- Predicting house prices based on features like area, number of rooms, location
- Estimating sales based on advertising spend
- Forecasting stock prices or demand
- Predicting student scores based on study hours

---

## Example 1: Simple Linear Regression with NumPy

Let's fit a line to some sample data using only NumPy.

```python
import numpy as np
import matplotlib.pyplot as plt

# Sample data
x = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 5, 4, 5])

# Calculate coefficients
m, c = np.polyfit(x, y, 1)
print(f"Slope: {m:.2f}, Intercept: {c:.2f}")

# Predict values
y_pred = m * x + c

# Plot
plt.scatter(x, y, color='blue', label='Actual')
plt.plot(x, y_pred, color='red', label='Predicted')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.title('Simple Linear Regression')
plt.show()
```

---

## Example 2: Linear Regression with scikit-learn

The `scikit-learn` library provides a simple interface for linear regression.

```python
from sklearn.linear_model import LinearRegression
import numpy as np
import matplotlib.pyplot as plt

# Data
x = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)
y = np.array([2, 4, 5, 4, 5])

# Model
model = LinearRegression()
model.fit(x, y)

print(f"Slope: {model.coef_[0]:.2f}")
print(f"Intercept: {model.intercept_:.2f}")

# Predict
y_pred = model.predict(x)

# Plot
plt.scatter(x, y, color='blue', label='Actual')
plt.plot(x, y_pred, color='red', label='Predicted')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.title('Linear Regression with scikit-learn')
plt.show()
```

---

## Evaluating the Model

Common metrics for linear regression:
- **Mean Squared Error (MSE):** Average squared difference between actual and predicted values.
- **R² Score (Coefficient of Determination):** Proportion of variance explained by the model (1 is perfect).

```python
from sklearn.metrics import mean_squared_error, r2_score

mse = mean_squared_error(y, y_pred)
r2 = r2_score(y, y_pred)
print(f"MSE: {mse:.2f}")
print(f"R² Score: {r2:.2f}")
```

---

## Multiple Linear Regression

When you have more than one feature:

```python
import numpy as np
from sklearn.linear_model import LinearRegression

# Features: x1 and x2
X = np.array([
    [1, 2],
    [2, 1],
    [3, 4],
    [4, 3],
    [5, 5]
])
y = np.array([3, 3, 7, 7, 10])

model = LinearRegression()
model.fit(X, y)

print("Coefficients:", model.coef_)
print("Intercept:", model.intercept_)
```

---


---

## Multiple Choice Questions

1. What is the main goal of linear regression?
    a) Classify data into categories
    b) Predict continuous values
    c) Cluster data into groups
    d) Reduce dimensionality

2. Which metric is commonly used to evaluate linear regression?
    a) Accuracy
    b) Mean Squared Error (MSE)
    c) Silhouette Score
    d) F1 Score

3. What does the slope (m) represent in the equation $y = mx + c$?
    a) The predicted value
    b) The input feature
    c) The rate of change of y with respect to x
    d) The intercept

4. Which of the following is NOT a real-life application of linear regression?
    a) Predicting house prices
    b) Image classification
    c) Forecasting sales
    d) Predicting exam scores

---

## Reflective Questions
- How would you use linear regression to predict the price of a used car?
- What features would you consider for predicting house prices?
- Can you think of a scenario where linear regression would not be appropriate?

---

## Practice Exercise

**Task:**
- Generate random data for $x$ and $y$ where $y = 2x + 1 +$ some noise.
- Fit a linear regression model and plot the results.

**Starter code:**
```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

np.random.seed(0)
x = np.random.rand(50, 1) * 10
noise = np.random.randn(50, 1)
y = 2 * x + 1 + noise

model = LinearRegression()
model.fit(x, y)
y_pred = model.predict(x)

plt.scatter(x, y, color='blue', label='Actual')
plt.plot(x, y_pred, color='red', label='Predicted')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.title('Practice: Linear Regression')
plt.show()
```

---

## Key Points
- Linear regression is used for predicting continuous values.
- The model finds the best-fit line by minimizing the error.
- Use libraries like NumPy for simple cases, and scikit-learn for real-world problems.
- Always evaluate your model using metrics like MSE and R².

---

## Further Reading
- [scikit-learn LinearRegression documentation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- [Visual Introduction to Linear Regression](https://www.datacamp.com/tutorial/linear-regression-python)
