# Advanced Density-Based Clustering: HDBSCAN vs DBSCAN
**Unsupervised Learning Project**

## Project Overview
This repository contains the final project for the Unsupervised Learning course.

The study focuses on Manifold Learning and Density-Based Clustering, providing a critical analysis of the **DBSCAN** algorithm's limitations when processing heterogeneous data structures. It subsequently demonstrates the topological robustness of **HDBSCAN** (Hierarchical Density-Based Spatial Clustering of Applications with Noise) as a superior alternative for complex datasets.

## Theoretical Framework

### The "Variable Density" Problem
Classical density-based algorithms, such as DBSCAN, rely on a global parameter, epsilon ($\epsilon$), to define the neighborhood radius for cluster formation. This approach operates on the assumption that a single density threshold is valid for the entire dataset.

In real-world scenarios, however, data often exhibits multi-scale structures where high-density clusters coexist with sparse ones. This creates a fundamental trade-off:
* **Low $\epsilon$:** Maximizes precision for dense clusters but fails to capture sparse structures (classifying them as noise).
* **High $\epsilon$:** Maximizes recall for sparse structures but incorrectly merges distinct dense clusters into single entities.

### The HDBSCAN Solution
HDBSCAN resolves this limitation by transforming the clustering task into a hierarchical optimization problem. Instead of applying a fixed horizontal cut across the density landscape, the algorithm:
1.  Constructs a hierarchy of all possible clusterings (Condensed Cluster Tree).
2.  Estimates the **stability** (persistence) of each cluster across varying density levels.
3.  Extracts the optimal clustering configuration that maximizes stability, effectively adapting to local density variations without requiring a global threshold.

## Experimental Results
The analysis, detailed in `HDBSCAN_project.ipynb`, utilizes synthetic datasets generated via a Gaussian Mixture Model to simulate variable densities.

**Key Findings:**
1.  **DBSCAN Limitation:** Empirical testing confirms that for a dataset with mixed standard deviations (e.g., $\sigma=0.5$ and $\sigma=2.5$), no single $\epsilon$ value can simultaneously segment all groups correctly.
2.  **HDBSCAN Robustness:** By prioritizing cluster stability over fixed geometry, HDBSCAN successfully identifies all structures regardless of their local density, requiring only a minimum cluster size parameter.

## Repository Contents

* **HDBSCAN_project.ipynb**: The primary Jupyter Notebook containing the algorithmic implementation, visualization logic, and comparative analysis.
* **UL project.pdf**: A comprehensive PDF report generated from the notebook, suitable for offline review.
* **README.md**: Documentation and project specifications.

## Installation and Usage

To reproduce the analysis locally, ensure the Python environment meets the following requirements.

### Prerequisites
* Python 3.8+
* hdbscan
* numpy
* matplotlib
* seaborn
* scikit-learn

### Setup
1.  Clone the repository:
    ```bash
    git clone [https://github.com/](https://github.com/)[your-username]/HDBSCAN-Analysis.git
    ```
2.  Install dependencies:
    ```bash
    pip install hdbscan numpy matplotlib seaborn scikit-learn
    ```
3.  Launch the notebook:
    ```bash
    jupyter notebook HDBSCAN_project.ipynb
    ```

*This analysis adheres to the theoretical guidelines provided in the course lectures and utilizes the official hdbscan library implementation.*
