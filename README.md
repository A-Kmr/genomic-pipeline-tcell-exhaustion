# Genomic Data Pipeline: T-Cell Exhaustion Analysis

## 🧬 Project Overview
This project builds a computational pipeline to analyze single-cell RNA sequencing (scRNA-seq) data, specifically focusing on identifying and characterizing **T-Cell Exhaustion** in cancer environments. 

### Current Progress: Phase 1 (Healthy Baseline)
In Phase 1, I successfully architected the core pipeline using **Scanpy** and **Google Colab (GPU-accelerated)**. I utilized a healthy PBMC (Peripheral Blood Mononuclear Cell) dataset to establish a biological "ground truth" before moving into comparative cancer analysis.

---

## 🛠️ Pipeline Architecture (Phase 1)

### 1. Data Ingestion (Bronze Layer)
* **Dataset:** 3,000 Healthy PBMCs (Peripheral Blood Mononuclear Cells).
* **Initial Dimensions:** 2,700 cells across 32,738 genes.
* **Tooling:** Leveraged `scanpy.datasets` for direct ingestion into an `AnnData` object.

### 2. Quality Control & Preprocessing (Silver Layer)
To ensure high-fidelity results, I implemented rigorous QC filters:
* **Mitochondrial Filtering:** Removed dying cells with >5% mitochondrial gene expression.
* **Doublet/Debris Removal:** Filtered cells with extreme gene counts (>2500 or <200).
* **Final Cleaned Count:** **2,638 high-quality cells.**

### 3. Feature Selection & Normalization
* **Normalization:** Scaled counts to 10,000 per cell to account for varying sequencing depth.
* **Log-Transformation:** Applied `log1p` to linearize biological variance.
* **HVG Selection:** Identified the **2,013 Highly Variable Genes** to reduce computational noise by ~94%.

### 4. Dimensionality Reduction & Clustering (Gold Layer)
* **PCA:** Reduced features to 50 Principal Components.
* **UMAP:** Generated 2D visualizations for spatial manifold representation.
* **Leiden Clustering:** Identified **6 distinct cell communities** using a resolution of 0.5.

---

## 🔬 Biological Results
Through marker gene analysis, I scientifically validated the clusters:
* **T-Cells (Cluster 0):** Identified via high expression of the **CD3E** marker gene.
* **B-Cells (Cluster 1):** Identified via **MS4A1** (CD20) expression.
* **NK Cells:** Identified via **NKG7/GNLY** expression.

<img width="350" height="252" alt="image" src="https://github.com/user-attachments/assets/883cc75a-c3fe-4959-9c47-e8c7b03e5f30" />


---

## 🚀 Technical Skills Demonstrated
* **Environment:** Google Colab (GPU Runtime), Python 3.x.
* **Libraries:** Scanpy, Pandas, Numpy, Matplotlib, Leidenalg.
* **Data Science:** PCA, UMAP, Unsupervised Clustering, Data Cleaning.
* **Bioinformatics:** Single-cell RNA-seq processing, Gene expression normalization.
