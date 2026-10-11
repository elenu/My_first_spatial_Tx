# My_first_spatial_Tx

This repository documents my first attempt at spatial transcriptomics analysis by reproducing a published study on endometriosis.

## Overview

Endometriosis affects approximately 1 in 10 women of reproductive age and is a chronic, inflammatory disease characterized by the growth of endometrial-like tissue outside the uterus, leading to pain, infertility, and significant reduction in quality of life. From a Biopharma standpoint, addressing endometriosis is challenging due to its heterogeneous symptoms, variable response to treatment, and incomplete understanding of underlying mechanisms. Innovative companies are focused on developing novel medical therapies that go beyond traditional hormonal and anti-inflammatory drugs. These efforts include the discovery of compounds targeting key inflammatory pathways, immune responses, and angiogenesis processes implicated in lesion growth and maintenance. Clinical development programs increasingly integrate patient-reported outcomes to capture the full scope of disease burden and guide personalized therapy. 

Omics and bioinformatics are revolutionizing endometriosis research. Genomic studies help identify susceptibility loci and genetic variants linked to disease onset, progression, and drug response. Transcriptomic and proteomic analyses reveal dysregulated signaling pathways and molecular signatures differentiating endometriosis lesions from healthy tissue, illuminating novel therapeutic targets and mechanisms of resistance. Integration of multi-omics data with advanced bioinformatics allows for the stratification of patient populations, the discovery of non-invasive diagnostic biomarkers, and the tailoring of treatment regimens to individual profiles. 

The approach of the project taken as a reference is studying spatinal transcriptomics, since despite its prevalence, the immune landscape of endometriotic lesions remains poorly characterized at single-cell resolution. The project taken as reference (<https://github.com/taimcnugget/endo-immune-atlas>) integrates scRNA-seq and spatial transcriptomics to map immune cell states, with a focused analysis on immunosenescence  the acquisition of a senescent phenotype by immune cells  within ectopic, eutopic, and healthy endometrial tissue.

My aim has been to adapt the project's code reproduce the results prublished in the authors' publication, a reproducible Snakemake pipeline for spatial immune and immunosenescence profiling in endometriosis using public single-cell and spatial transcriptomics data: <https://github.com/taimcnugget/endo-immune-atlas>. I have also explored different gene lists as alternative to observe potential value to new insights (not shown).

I organized script in this repo as a step-by-step workflow in the `scr/` folder, moving from data collection to downstream spatial interpretation, following the flowstream of the authors of the study to answer biological questions:

1. How do immune cell states differ across ectopic, eutopic, and healthy endometrium?
2. Are immunosenescent populations enriched in endometriotic lesions?
3. How do senescence-high immune cells spatially organize within the lesion microenvironment?
4. What ligand-receptor interactions are enriched between senescent immune cells and other cell types in the lesion niche?

## Data

Datasets used by the authors of the study:

| Accession | Type | Description |
|---|---|---|
| GSE179640 | scRNA-seq | Ectopic, eutopic, and healthy endometrium (Tan et al.) |
| GSM6690475 / GSM6690476 | Visium ST | Ectopic endometriosis lesion tissue sections |

## Workflow of updated scripts

### Single-cell data processing
- `00_spatial_data_collection.ipynb` — collection/preparation of spatial data.
- `01_sc_data_collection.ipynb` — collection/preparation of single-cell data.
- `02_sc_quality_control.ipynb` — single-cell quality control.
- `03_sc_integration.ipynb` — integration of single-cell datasets.
- `04_sc_clustering.ipynb` — clustering of single-cell data.
- `05_sc_immune_annotation.ipynb` — immune cell annotation.
- `05_sc_immune_annotation_test.ipynb` — immune cell annotation with my contribution on EGCs.
- `06_sc_immunosenescence.ipynb` — analysis of immunosenescence in single-cell data.

### Spatial analysis
- `07_spatial_cell2location.ipynb` — cell2location-based mapping of cell types into spatial data.
- `08_spatial_immune_architecture.ipynb` — analysis of spatial immune architecture.
- `09_spatial_immunosenescence.ipynb` — spatial analysis of immunosenescence signatures.
- `10_spatial_niche_discovery.ipynb` — discovery of spatial niches.
- `12_spatial_niche_ccc.ipynb` — cell-cell communication analysis in spatial niches.

### Cell-cell communication
- `11_sc_ccc.ipynb` — cell-cell communication analysis in the single-cell data.

## Conclusion and key findings

Here I confirm code is reproducible and useful. I have observed we can customice biomarkers lists and explore more gene sets of different immune annotations or cell-cell communication. I also tested known associated biomarkers such as Entero Glia Cells biomarkers, which are expected to be elevated in endometriosis (<https://doi.org/10.1186/s12905-024-03480-7>).

I encourage other scientists to use it because the analysis of samples associated to endometriosis will allow to leverage these insights to accelerate the development of new therapeutics, improve diagnostics, and promote more precise and effective care for women affected by endometriosis. 

## Notes

The notebooks in `scr/` are intended to be run in sequence, with each stage building on the results of the previous one.

Most of my updates were associated to kernel and module loading, but also simplified workload reducing PCA components from 50 to 30.
