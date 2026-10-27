# 03 — DBSCAN Clustering

Open **[DBSCAN clustering](01_dbscan_clustering.ipynb)** after K-Means and hierarchical clustering.

## What to learn

- DBSCAN forms clusters from dense neighborhoods rather than centroids.
- `eps` sets the neighborhood radius.
- `min_samples` controls the minimum number of nearby samples required to form a core point.
- Samples labelled `-1` are treated as noise by Scikit-learn's implementation.
- DBSCAN does not require the number of clusters to be specified in advance and can identify density-connected non-linear groups.
- Scaling and parameter choices can substantially change the result.

## Official references

- [Scikit-learn clustering guide](https://scikit-learn.org/stable/modules/clustering.html#dbscan)
- [DBSCAN API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)
