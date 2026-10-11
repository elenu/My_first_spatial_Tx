# My_first_spatial_Tx

This repository documents my first attempt at spatial transcriptomics analysis by reproducing a published study on endometriosis.

## Overview

Endometriosis affects approximately 1 in 10 women of reproductive age and is a chronic, inflammatory disease characterized by the growth of endometrial-like tissue outside the uterus, leading to pain and infertility. Despite its prevalence, the immune landscape of endometriotic lesions remains poorly characterized at the single-cell and spatial level.

Omics and bioinformatics are revolutionizing endometriosis research. Genomic studies help identify susceptibility loci and genetic variants linked to disease onset, progression, and drug response. Transcriptomic approaches, particularly single-cell and spatial transcriptomics, enable high-resolution characterization of cell states and tissue organization in endometrial tissues.

This project takes a spatial transcriptomics approach to study the immune microenvironment of endometriotic lesions. The analysis is based on a reproducible Snakemake pipeline for spatial immune and immunosenescence profiling in endometriosis, adapted from the original published study.

The scripts in this repository are organized as a step-by-step workflow in the `scr/` folder, progressing from data collection to downstream spatial interpretation, following the methodology of the original study authors.

### Research Questions

1. How do immune cell states differ across ectopic, eutopic, and healthy endometrium?
2. Are immunosenescent populations enriched in endometriotic lesions?
3. How do senescence-high immune cells spatially organize within the lesion microenvironment?
4. What ligand-receptor interactions are enriched between senescent immune cells and other cell types in the lesion niche?

## Data

Datasets used by the original study authors:

| Accession | Type | Description |
|---|---|---|
| GSE179640 | scRNA-seq | Ectopic, eutopic, and healthy endometrium (Tan et al.) |
| GSM6690475 / GSM6690476 | Visium ST | Ectopic endometriosis lesion tissue sections |

## Workflow

### Single-cell data processing
- `00_spatial_data_collection.ipynb` — Collection and preparation of spatial data
- `01_sc_data_collection.ipynb` — Collection and preparation of single-cell data
- `02_sc_quality_control.ipynb` — Single-cell quality control
- `03_sc_integration.ipynb` — Integration of single-cell datasets
- `04_sc_clustering.ipynb` — Clustering of single-cell data
- `05_sc_immune_annotation.ipynb` — Immune cell annotation
- `06_sc_immunosenescence.ipynb` — Analysis of immunosenescence in single-cell data

### Spatial analysis
- `07_spatial_cell2location.ipynb` — Cell2location-based mapping of cell types into spatial data
- `08_spatial_immune_architecture.ipynb` — Analysis of spatial immune architecture
- `09_spatial_immunosenescence.ipynb` — Spatial analysis of immunosenescence signatures
- `10_spatial_niche_discovery.ipynb` — Discovery and characterization of spatial niches
- `12_spatial_niche_ccc.ipynb` — Cell-cell communication analysis in spatial niches

### Cell-cell communication
- `11_sc_ccc.ipynb` — Cell-cell communication analysis in single-cell data

## Key Findings and Contributions

### Workflow Reproducibility

This analysis confirms the reproducibility and utility of the original pipeline. The code has been adapted and simplified while maintaining scientific rigor, including:

- Streamlined kernel and module loading

- Optimized PCA components (reduced from 50 to 30) without loss of biological signal

### Observations on EGCs Biomarkers

**Important Finding**: During immune cell annotation, I observed that classical Entero Glia Cell (EGC) biomarkers showed limited discriminative power for this cell population. Specifically:

- EGC biomarkers were not clearly associated with the EGC cluster

- Expression levels of characteristic EGC markers were lower than expected based on literature

- This suggests potential limitations in using classical EGC markers for EGC identification in endometriotic tissue

This observation highlights the importance of validating canonical biomarkers in disease-specific contexts and may warrant further investigation into alternative or additional markers for eosinophil annotation in endometriosis samples.

### Opportunities for Extension

The codebase is flexible and allows for:

- Customization of biomarker lists for different cell types

- Exploration of alternative gene sets for immune annotation

- Extended cell-cell communication analyses with different interaction databases

## Conclusion

This reproducible workflow demonstrates the applicability of spatial transcriptomics and immunosenescence profiling to endometriosis research. Analysis of endometriosis samples using this pipeline can provide insights to accelerate the development of new therapeutics, improve diagnostic approaches, and enhance our understanding of the disease mechanisms.

I encourage other scientists to use and adapt this pipeline, explore other tissue sections, and to contribute additional insights that may help overcome current limitations in marker-based cell annotation.

## Technical Notes

- All notebooks, except the one associated to my contribution (`04_sc_clustering_test.ipynb` and `05_sc_immune_annotation_test.ipynb`), in `scr/` are intended to be run sequentially, with each stage building on the results of the previous one. 

- Python environment and dependencies are specified in the project configuration

- Outputs from each notebook stage are saved for downstream analysis

---

**Original Study Reference**: <https://github.com/taimcnugget/endometriosis-spatial-immune-atlas>

**Entero Glia Cells Reference**: <https://doi.org/10.1186/s12905-024-03480-7>
