# Unsupervised Learning — Part 2

This repository is the **second and final part** of the unsupervised learning study path. Part 1 covers clustering fundamentals (K-Means, the Elbow Method, silhouette score, hierarchical clustering, dendrograms, and DBSCAN). This part completes the learning path with **Principal Component Analysis (PCA)** and **anomaly detection**.

The uploaded notebooks are retained as the starting material and organized by topic. The notebook names are clearer, and the section guides explain the suggested order. The originals are not intended to imply clinical or operational readiness: these are learning exercises.

## Learning path

### 01. Principal Component Analysis (PCA)

Start with [PCA step by step on Iris](01-PCA/01_pca_iris_step_by_step.ipynb).

Topics:
- Load the Iris dataset and separate feature measurements from species labels.
- Standardize features before PCA.
- Fit PCA and transform the data into principal components.
- Inspect transformed dimensions, explained variance ratios, and component vectors.
- Visualize the first two principal components.

PCA is a dimensionality-reduction technique; it does not itself perform clustering or detect anomalies. In this learning notebook, Iris labels are used only to color the plot for interpretation.

Official documentation: [Scikit-learn PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) · [PCA user guide](https://scikit-learn.org/stable/modules/decomposition.html#pca)

### 02. Anomaly Detection

Then explore [Isolation Forest and Local Outlier Factor (LOF)](02-Anomaly-Detection/02_isolation_forest_and_lof.ipynb).

Topics:
- Separate the supplied `Outlier_label` column from the input features.
- Standardize features.
- Use Isolation Forest to estimate outliers.
- Project the scaled features into two dimensions with PCA for visualization.
- Count normal and outlier predictions.
- Compare with Local Outlier Factor (LOF).

The supplied `thyroid_dataset.csv` contains **6,916 rows and 22 columns**. Its `Outlier_label` column contains `n` (6,666 rows) and `o` (250 rows). In the original notebook, this label is separated from `X`, while the unsupervised estimators fit on `X_scaled`. Treat the column as a reference label for later comparison rather than a feature.

Prediction conventions matter: in Scikit-learn's Isolation Forest and LOF, `1` means inlier and `-1` means outlier. These predictions are not the same as the CSV's string labels `n` and `o`. Contamination is an estimate/parameter for the expected proportion of outliers, not a guarantee that every detected point is truly anomalous.

Official documentation: [IsolationForest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html) · [LocalOutlierFactor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.LocalOutlierFactor.html)

### 03. DBSCAN as a density-based method

Read [DBSCAN on non-linear moons data](02-Anomaly-Detection/03_dbscan_density_based_anomaly_context.ipynb) to connect clustering with density-based identification of noise points.

Topics:
- Generate non-linear sample data with `make_moons`.
- Standardize features.
- Fit DBSCAN using `eps` and `min_samples`.
- Visualize the cluster labels, including label `-1` for noise.

DBSCAN is first and foremost a clustering algorithm. It can mark low-density points as noise, but that use is not the same as a dedicated outlier detector such as Isolation Forest or LOF.

Official documentation: [DBSCAN](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)

## Repository structure

```text
unsupervised-learning-part-2/
├── 01-PCA/
│   └── 01_pca_iris_step_by_step.ipynb
├── 02-Anomaly-Detection/
│   ├── 02_isolation_forest_and_lof.ipynb
│   └── 03_dbscan_density_based_anomaly_context.ipynb
├── data/
│   └── thyroid_dataset.csv
├── docs/
│   └── ANOMALY_DETECTION_AND_PCA_REFERENCES.md
├── requirements.txt
├── LICENSE
└── README.md
```

## Setup

Python 3.10 or newer is recommended.

```bash
python -m venv .venv
```

Activate the environment, then install dependencies:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Run notebooks from top to bottom. The anomaly notebook reads `thyroid_dataset.csv` from the repository's `data/` folder. If you run the notebook directly from its topic folder, use the relative path `../data/thyroid_dataset.csv` or start Jupyter from the repository root and update the dataset path accordingly.

## References

See [PCA and anomaly-detection concept notes](docs/ANOMALY_DETECTION_AND_PCA_REFERENCES.md) for definitions, differences, and official documentation links.

## Important note

This is an educational machine-learning repository. The thyroid data and anomaly predictions should not be used for diagnosis or healthcare decisions. An anomaly is a point that differs from a learned pattern; it is not automatically erroneous, fraudulent, unhealthy, or clinically important.