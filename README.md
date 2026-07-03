# SIRCL
## A Flexible and Robust Pipeline for NMR Chemometric Feature Selection, Dimension Reduction, and Clustering

An interactive, web-based pipeline for high-dimensional spectral data exploration, pretreatment, dimension reduction, and unsupervised clustering.

---

## 🚀 Key Steps of the Pipeline

* **Flexible Data Ingestion:** Supports `.csv`, `.txt`, and `.xlsx` files. Dynamically handles regional formatting variations, including European/German decimal comma representations.
* **Metadata Splitting:** Slices raw matrices to decouple experimental metadata (sample IDs, groups, hover labels) from high-dimensional numeric measurement channels.
* **Dynamic Noise Filtering:** Column-wise feature selection based on maximum signal percentage thresholds to exclude flat baselines and instrument noise.
* **Advanced Pretreatment (SpImp):** Implements **Spectral Importance Partitioning and Imputation (SpImp)**, a vectorized row-wise and column-wise normalization algorithm designed to amplify rare yet distinguishing sample markers.
* **Interactive Dimensionality Reduction:** Utilizes Uniform Manifold Approximation and Projection (**UMAP**) with dynamic control over hyperparameters (neighbors, minimum distance, and target component dimensions).
* **Unsupervised Class Mapping:** Integrates Hierarchical Density-Based Spatial Clustering of Applications with Noise (**HDBSCAN**) to assign sample categories and evaluate structural probability densities without forcing data points into arbitrary cluster totals.
* **Publication-Ready Figures:** Compare raw vs. processed spectra using native side-by-side diagnostic charts. Customize scatter plots with responsive categorical hexadecimal colors and download high-resolution vector visuals as **SVG** files.

---

## 📂 Repository Structure

```text
├── main.py             # App entry point, orchestrates execution flow & session state
├── BfR_Logo.png        # Institutional or project branding image
├── requirements.txt    # Python packages required for deployment
└── src/
    ├── customtools.py  # Math & ML processing core (SpImp, UMAP execution, HDBSCAN)
    ├── forms.py        # Isolated, high-performance Streamlit form widgets
    └── visual.py       # Vector figure generators & plotting utilities (Plotly)
```

## 📊 Methodology

The core data transformation layer implements the **SpImp** (Species Importance) filtering:

$$\text{SpImp}_{ij} = \left( \frac{x_{ij}}{\text{SF}_i} \right) \times \log_{10}\left(\frac{N + 1}{nt_j + 1}\right)$$

**Where:**
* $x_{ij}$ = Signal intensity of sample $i$ at variable $j$.
* $\text{SF}_i$ = Row-wise sum of all measurement values within sample $i$.
* $N$ = Total sample size in the experimental dataset.
* $nt_j$ = Column-wise total count of samples exhibiting non-zero detection at variable $j$.

## 🌐 Web application

Data processing with the SIRCL pipeline is available at https://sircl-analytics.streamlit.app/
