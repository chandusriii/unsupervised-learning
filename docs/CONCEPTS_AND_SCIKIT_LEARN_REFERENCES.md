# Unsupervised Learning Concepts and Scikit-learn References

This repository provides hands-on practice with clustering algorithms. Use feature measurements to fit unsupervised models; Iris species labels should only be used for a post-clustering comparison.

## K-Means

K-Means partitions observations into a selected number of clusters represented by centroids. It alternates between assigning observations to nearby centroids and updating centroids to reduce within-cluster sum of squares (inertia).

- API: https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
- Clustering guide: https://scikit-learn.org/stable/modules/clustering.html#k-means

### Choosing K: inertia, Elbow Method, and silhouette

The Elbow Method plots inertia across candidate values of K and looks for a point where adding clusters provides diminishing reductions in inertia. Inertia generally decreases as K increases, so simply choosing the smallest value is not meaningful.

Silhouette score compares the distance of each sample to its own cluster with its distance to the nearest alternative cluster. It ranges from -1 to +1. Interpret it alongside visualizations and the data context.

- Silhouette API: https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html

## Hierarchical / Agglomerative Clustering

Agglomerative clustering starts with individual observations and repeatedly merges clusters according to a linkage criterion. A dendrogram displays the hierarchy and merge distances.

- Ward linkage minimizes the increase in within-cluster variance and requires Euclidean distance.
- Complete linkage uses the maximum pairwise distance between two clusters.
- Average linkage uses the average pairwise distance between two clusters.
- Single linkage uses the minimum pairwise distance between two clusters.

Scikit-learn's `AgglomerativeClustering` produces cluster labels. SciPy's hierarchy functions can be used to generate a dendrogram.

- Scikit-learn clustering guide: https://scikit-learn.org/stable/modules/clustering.html#hierarchical-clustering
- AgglomerativeClustering API: https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html
- SciPy dendrogram API: https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html

## DBSCAN

DBSCAN groups observations in dense regions and labels observations that do not belong to dense regions as noise (`-1`). It does not require the number of clusters in advance and can identify non-convex density-connected groups.

- `eps`: neighborhood radius.
- `min_samples`: minimum neighborhood sample count needed for a core point, including the point itself in Scikit-learn's convention.

Feature scaling and parameter selection can strongly affect the result.

- DBSCAN API: https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html

## K-Means vs. Hierarchical Clustering vs. DBSCAN

| Property | K-Means | Hierarchical / Agglomerative | DBSCAN |
|---|---|---|---|
| Choose cluster count before fitting? | Yes | Choose a count or cut the hierarchy for a flat solution | No |
| Main mechanism | Centroids and distance minimization | Repeated merging under a linkage rule | Density-connected neighborhoods |
| Explicit noise label | No | No | Yes, label `-1` |
| Non-convex groups | Often struggles | Depends on linkage and data | Often suitable for density-connected shapes |
| Important choices | K, initialization, scaling | Linkage, distance, cluster count/cut | eps, min_samples, scaling |

No method is best for every dataset. Compare assumptions, visual patterns, and evaluation measures.

## Iris data and label leakage

For an unsupervised exercise, fit clustering only on Iris feature measurements. Known species labels should not be passed to the clustering estimator during fitting. They can be compared with cluster assignments afterward as an educational analysis. Cluster IDs are arbitrary and do not inherently correspond to species names.

## General references

- Scikit-learn Unsupervised Learning: https://scikit-learn.org/stable/unsupervised_learning.html
- Scikit-learn Clustering: https://scikit-learn.org/stable/modules/clustering.html
