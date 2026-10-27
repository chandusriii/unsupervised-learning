# Unsupervised Learning

A hands-on collection of Python notebooks exploring unsupervised machine learning with Scikit-learn. Topics include K-Means clustering, the Elbow Method, inertia, silhouette score, hierarchical clustering, dendrograms, DBSCAN, and cluster visualizations.

## Notebooks

- `KMeans.ipynb` — K-Means concepts and implementation.
- `KMeansForIris.ipynb` — K-Means clustering using the Iris dataset.
- `hierarchical_clustering.ipynb` — hierarchical clustering and dendrograms.
- `DBSCAN.ipynb` — density-based clustering and noise points.

## Topics

- Clustering fundamentals and feature scaling
- Choosing K with inertia and the Elbow Method
- Evaluating separation with silhouette score
- Hierarchical/agglomerative clustering and dendrograms
- K-Means vs. hierarchical clustering
- DBSCAN parameters (`eps`, `min_samples`) and noise detection
- Visualizing clusters and interpreting results

## Setup

Python 3.10+ is recommended.

```bash
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Open a notebook and run its cells from top to bottom.

## Official documentation

- [Scikit-learn: Unsupervised learning](https://scikit-learn.org/stable/unsupervised_learning.html)
- [Scikit-learn: Clustering](https://scikit-learn.org/stable/modules/clustering.html)
- [KMeans API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [AgglomerativeClustering API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html)
- [DBSCAN API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)
- [Silhouette score API](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html)
- [SciPy dendrogram API](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)

## Note

For the Iris clustering examples, use feature measurements to fit unsupervised algorithms. Species labels can be used for post-clustering comparison, but should not be used as input labels when fitting the clustering model.
