# 01 — K-Means Clustering

Study these notebooks in order:

1. **[K-Means on generated blobs](01_kmeans_blobs_elbow_silhouette.ipynb)** — understand centroids and cluster labels, then examine inertia/WCSS, the Elbow Method, and silhouette score.
2. **[K-Means on Iris](02_kmeans_iris.ipynb)** — apply the algorithm to the Iris measurements and inspect the resulting clusters.

## Core ideas

- K-Means partitions observations into a selected number of clusters represented by centroids.
- Inertia (within-cluster sum of squares / WCSS in many teaching materials) summarizes squared distances from observations to their assigned centroids.
- The Elbow Method looks for diminishing improvement as K increases; the elbow may be ambiguous.
- Silhouette score ranges from -1 to +1 and evaluates how separated clusters are under a chosen distance metric.
- Since K-Means is distance-based, feature scaling is often important when features use different scales.

## Official references

- [K-Means guide](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- [KMeans API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [Silhouette score API](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html)
