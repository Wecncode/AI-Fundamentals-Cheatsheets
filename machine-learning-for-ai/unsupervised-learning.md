# Unsupervised Learning

Unsupervised learning identifies patterns, groupings, or structures in datasets without pre-existing labels.

## 1. Clustering Algorithms

| Algorithm | Mechanism | Best Use Case | Weakness |
|---|---|---|---|
| **K-Means** | Partitions data into $K$ distinct clusters based on distance to centroids. | Spherical, evenly sized clusters. Market segmentation. | Requires pre-defining $K$; sensitive to outliers. |
| **Hierarchical** | Builds a tree of clusters (dendrogram) bottom-up or top-down. | Unknown cluster counts; taxonomy creation. | Computationally expensive for large datasets. |
| **DBSCAN** | Groups dense regions of points, marking low-density regions as noise. | Arbitrary shaped clusters; spatial data. | Struggles with varying density clusters. |

### K-Means Objective Function (Inertia)
Minimizes the within-cluster sum of squares (WCSS):
$$WCSS = \sum_{j=1}^{K} \sum_{i \in C_j} ||x_i - \mu_j||^2$$
*(Where $\mu_j$ is the centroid of cluster $C_j$)*

## 2. Dimensionality Reduction

Techniques to reduce the number of features while retaining maximum information variance.

### Principal Component Analysis (PCA)
Projects data onto a lower-dimensional space using eigenvectors of the covariance matrix.
*   **Goal:** Maximize variance, minimize projection error.
*   **Process:** 
    1. Standardize data.
    2. Compute covariance matrix.
    3. Calculate eigenvalues/eigenvectors.
    4. Select top $k$ eigenvectors.

### t-SNE & UMAP
Non-linear dimensionality reduction techniques primarily used for 2D/3D visualization of high-dimensional data (e.g., word embeddings, genetic data). Preserves local structure better than PCA.

*©️ Created by Wecncode Developer Community!* 
