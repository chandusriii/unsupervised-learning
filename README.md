# Unsupervised Machine Learning

A hands-on learning repository for **Unsupervised Learning with Python and Scikit-learn**. It follows a topic-by-topic learning path, from K-Means fundamentals to hierarchical clustering and density-based clustering.

The notebooks are organized in the order you can study them. The original notebooks you supplied are retained; they have been moved into clearly named topic folders rather than mixed together at the repository root.

## Learning path

### 01. K-Means Clustering

Start with K-Means on generated blob data, then move to the Iris dataset.

| Resource | Topics |
|---|---|
| [K-Means fundamentals, Elbow Method, and Silhouette Score](01-KMeans/01_kmeans_blobs_elbow_silhouette.ipynb) | Centroids, cluster labels, inertia/WCSS, choosing K, Elbow Method, silhouette score |
| [K-Means with the Iris dataset](01-KMeans/02_kmeans_iris.ipynb) | Load Iris features, scale features, fit K-Means, inspect and visualize cluster assignments |
| [K-Means section guide](01-KMeans/README.md) | Learning order and concept notes |

### 02. Hierarchical Clustering

Learn agglomerative clustering and how to read a dendrogram.

| Resource | Topics |
|---|---|
| [Hierarchical clustering and dendrogram](02-Hierarchical-Clustering/01_hierarchical_clustering_dendrogram.ipynb) | Feature scaling, linkage, hierarchical merging, dendrogram |
| [Hierarchical clustering guide](02-Hierarchical-Clustering/README.md) | How the method works and what to inspect |

### 03. DBSCAN

Study density-based clustering, including core points, noise, and non-linear datasets.

| Resource | Topics |
|---|---|
| [DBSCAN clustering](03-DBSCAN/01_dbscan_clustering.ipynb) | `eps`, `min_samples`, cluster labels, noise points, non-linear data |
| [DBSCAN section guide](03-DBSCAN/README.md) | Parameter interpretation and learning notes |

### 04. Part 2 — PCA and Anomaly Detection

Continue with the [Part 2 learning path](Part-2/README.md), which covers PCA step by step, Isolation Forest, Local Outlier Factor (LOF), and DBSCAN noise points using the uploaded notebooks and thyroid dataset.

### 05. Concepts and official documentation

Use the [concepts and Scikit-learn references guide](docs/CONCEPTS_AND_SCIKIT_LEARN_REFERENCES.md) alongside the notebooks.

Official references:
- [Scikit-learn: Unsupervised learning](https://scikit-learn.org/stable/unsupervised_learning.html)
- [Scikit-learn: Clustering](https://scikit-learn.org/stable/modules/clustering.html)
- [KMeans API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [AgglomerativeClustering API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html)
- [DBSCAN API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)
- [Silhouette score API](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html)
- [SciPy dendrogram API](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)
- [Part 2 PCA and anomaly-detection references](Part-2/docs/ANOMALY_DETECTION_AND_PCA_REFERENCES.md)

## Setup

Python 3.10+ is recommended. From the repository directory:

```bash
python -m venv .venv
```

Activate the environment, then install dependencies and launch Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Open the notebooks in the order above and run their cells from top to bottom.

## Important note on Iris

Iris species labels are known labels. To keep the example genuinely unsupervised, use the feature measurements to fit K-Means. Species labels may be compared with cluster assignments afterward as a separate educational check; they should not be used as target labels during fitting. Cluster IDs are arbitrary and do not map automatically to species names.
