# PCA and Anomaly Detection — Concepts and Official References

This guide complements the Part 2 notebooks.

## PCA (Principal Component Analysis)
PCA is a linear dimensionality-reduction method that transforms features into orthogonal components ordered by explained variance.

Workflow: select features and keep reference labels separate; scale when features have different units/ranges; choose `n_components`; fit and transform; inspect `explained_variance_ratio_` and `components_`; visualize the projection while remembering that a 2D view loses information.

- [PCA API](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html)
- [PCA user guide](https://scikit-learn.org/stable/modules/decomposition.html#pca)
- [StandardScaler API](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html)

## Anomaly detection
An anomaly detector flags observations that differ from a learned pattern. An outlier is not automatically an error or a meaningful event; flagged rows require context and validation.

### Isolation Forest
Isolation Forest builds random partitions and flags samples that are relatively easy to isolate. Scikit-learn's `fit_predict` returns `1` for inliers and `-1` for outliers. `contamination` is used to set the outlier decision threshold; `n_estimators` controls the number of trees.

- [IsolationForest API](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html)

### Local Outlier Factor (LOF)
LOF compares the local density around a sample with the density around its neighbors. A sample in a substantially lower-density neighborhood can be flagged as an outlier. The supplied notebook uses `fit_predict` to label the fitted samples.

- [LocalOutlierFactor API](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.LocalOutlierFactor.html)

### DBSCAN as a density-based noise detector
DBSCAN is primarily a clustering algorithm. It groups dense regions and assigns `-1` to samples treated as noise. Noise may be useful for anomaly investigation, but is not equivalent to confirmed anomaly ground truth.

- [DBSCAN API](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)

## Method comparison

| Method | Primary role | Key settings | Interpretation |
|---|---|---|---|
| PCA | Reduce dimensions | `n_components` | Creates principal-component coordinates; does not label anomalies |
| Isolation Forest | Outlier detection | `n_estimators`, `contamination` | `1` inlier, `-1` outlier |
| Local Outlier Factor | Local-density outlier detection | `n_neighbors`, `contamination` | `1` inlier, `-1` outlier |
| DBSCAN | Density-based clustering | `eps`, `min_samples` | Cluster IDs; `-1` noise |

## Thyroid dataset notes
The supplied `thyroid_dataset.csv` has 6,916 rows and 22 columns; the `Outlier_label` column contains `n` and `o` reference values. The supplied notebook removes this column from the feature matrix before fitting the detectors. These labels and predictions are for educational exploration only and are not medically validated.
