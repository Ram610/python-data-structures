
# K-Means Clustering in Python

K-Means is an unsupervised machine learning algorithm used for clustering data into groups (clusters) based on feature similarity. It is widely used for customer segmentation, image compression, and pattern recognition.

---

## Real-Life Applications
- Customer segmentation in marketing
- Image compression
- Document clustering (grouping similar articles)
- Anomaly detection in network traffic

---

## What is K-Means Clustering?

K-Means partitions data into $k$ clusters by minimizing the sum of squared distances between data points and their assigned cluster centers (centroids).

**Algorithm Steps:**
1. Choose the number of clusters $k$.
2. Randomly initialize $k$ centroids.
3. Assign each data point to the nearest centroid.
4. Recompute centroids as the mean of assigned points.
5. Repeat steps 3-4 until convergence (no change in assignments or centroids).

---

## Example: K-Means with scikit-learn

```python
from sklearn.datasets import make_blobs
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

# Generate synthetic data
X, y_true = make_blobs(n_samples=300, centers=4, cluster_std=0.60, random_state=0)

# Fit KMeans
kmeans = KMeans(n_clusters=4, random_state=0)
kmeans.fit(X)
y_kmeans = kmeans.predict(X)

# Plot clusters
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, s=50, cmap='viridis')
centers = kmeans.cluster_centers_
plt.scatter(centers[:, 0], centers[:, 1], c='red', s=200, alpha=0.75, marker='X', label='Centroids')
plt.title('K-Means Clustering')
plt.legend()
plt.show()
```

---

## Choosing the Number of Clusters (Elbow Method)

The "elbow method" helps determine the optimal $k$ by plotting the sum of squared distances (inertia) for different $k$ values.

```python
inertia = []
for k in range(1, 10):
    kmeans = KMeans(n_clusters=k, random_state=0)
    kmeans.fit(X)
    inertia.append(kmeans.inertia_)

plt.plot(range(1, 10), inertia, marker='o')
plt.xlabel('Number of clusters (k)')
plt.ylabel('Inertia')
plt.title('Elbow Method for Optimal k')
plt.show()
```

---


---

## Multiple Choice Questions

1. What is the main goal of K-Means clustering?
    a) Predict continuous values
    b) Classify data into categories
    c) Group similar data points together
    d) Reduce dimensionality

2. What is the role of the centroid in K-Means?
    a) It is a data point
    b) It is the mean of assigned points in a cluster
    c) It is always at the origin
    d) It is the farthest point from the cluster

3. Which of the following is NOT a real-life application of K-Means?
    a) Customer segmentation
    b) Image compression
    c) Predicting exam scores
    d) Document clustering

4. What is a common method to choose the number of clusters in K-Means?
    a) Elbow method
    b) Cross-validation
    c) Grid search
    d) Random guessing

---

## Reflective Questions
- How would you use K-Means to segment customers for a marketing campaign?
- What features might be important for document clustering?
- Can you think of a scenario where K-Means would not work well?

---

## Practice Exercise

**Task:**
- Use the iris dataset from scikit-learn.
- Cluster the data into 3 groups and plot the results.

**Starter code:**
```python
from sklearn.datasets import load_iris
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

# Load data
iris = load_iris()
X = iris.data

# Fit KMeans
kmeans = KMeans(n_clusters=3, random_state=0)
y_kmeans = kmeans.fit_predict(X)

# Plot (using first two features for visualization)
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, cmap='viridis')
plt.xlabel(iris.feature_names[0])
plt.ylabel(iris.feature_names[1])
plt.title('K-Means Clustering on Iris Data')
plt.show()
```

---

## Key Points
- K-Means is fast and easy to implement.
- Sensitive to initial centroid placement and outliers.
- The number of clusters $k$ must be chosen in advance.

---

## Further Reading
- [scikit-learn KMeans documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [K-Means Clustering Tutorial](https://www.datacamp.com/tutorial/k-means-clustering-python)
