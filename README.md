# Hepatic-stellate-cell-filtering

A reproducible Scanpy-based workflow for preprocessing public human liver single-cell RNA-seq datasets and filtering high-confidence hepatic stellate cells (HSCs) for downstream integration and comparative analysis.**

**Presented at** THE 16TH AFOB REGIONAL SYMPOSIUM (ARS 2026)

## Purpose
Preprocess raw 10x Genomics data from three GEO datasets to extract high-purity Hepatic Stellate Cells (HSCs) for downstream integration.

## Datasets

| Dataset     | Samples                          | Cell subtype          | Disease status     | Cause of liver disease          |
|-------------|----------------------------------|-----------------------|--------------------|---------------------------------|
| GSE136103   | 18 samples (Healthy1–5, Cirrhotic1–5) | Healthy / Fibrotic   | Healthy / Cirrhotic| Healthy, NAFLD, ALD, PBC       |
| GSE282701   | 12 samples (P10–P15 tumor/adjacent) | HBV-neg / HBV-pos HCC | Hepatocellular carcinoma | HBV-negative / HBV-positive HCC |
| GSE166635   | 2 samples (HCC1, HCC2)           | Hepatic Progenitor Cells | Primary liver cancer | PLC (HCC)                      |

**Total after filtering**: 21,672 high-quality HSCs.

## Repository contents
- `GSE136103.ipynb` – preprocessing and HSC filtering for healthy and cirrhotic liver samples  
- `GSE282701.ipynb` – preprocessing and HSC filtering for HBV-related HCC samples  
- `GSE166635.ipynb` – preprocessing and HSC filtering for primary liver cancer samples 
- `README.md`
- `.gitignore`

## Pipeline 
1. Load matrix + features + barcodes
2. QC (genes >200, mt% <20%, doublet removal)
3. Normalization (10k scaling + log1p)
4. HVG, PCA, Harmony batch correction (per dataset)
5. Leiden clustering + UMAP
6. HSC state scoring (qHSC, A1_HSC, A2_HSC, INF_HSC)
7. Re-clustering the HSC compartment
8. Save `*_HSC_candidates.h5ad`

## How to run
1. Open notebook in Jupyter/VS Code/Colab
2. Run cells sequentially
3. Output: `GSExxxx_HSC_candidates.h5ad`

## Requirements
- Python 3.10
- scanpy, anndata, pandas, matplotlib, seaborn, harmonypy

## Outputs 
- GSE136103_HSC_candidates.h5ad
- GSE282701_HSC_candidates.h5ad
- GSE166635_HSC_candidates.h5ad

---
