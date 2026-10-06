# My_first_spatial_Tx

This repository documents my first attempt at spatial transcriptomics analysis by reproducing a published study on endometriosis.

## Overview

The project is organized as a step-by-step workflow in the `scr/` folder, moving from data collection to downstream spatial interpretation.

## Workflow

### Single-cell data processing
- `00_spatial_data_collection.ipynb` — collection/preparation of spatial data.
- `01_sc_data_collection.ipynb` — collection/preparation of single-cell data.
- `02_sc_quality_control.ipynb` — single-cell quality control.
- `03_sc_integration.ipynb` — integration of single-cell datasets.
- `04_sc_clustering.ipynb` — clustering of single-cell data.
- `05_sc_immune_annotation.ipynb` — immune cell annotation.
- `06_sc_immunosenescence.ipynb` — analysis of immunosenescence in single-cell data.

### Spatial analysis
- `07_spatial_cell2location.ipynb` — cell2location-based mapping of cell types into spatial data.
- `08_spatial_immune_architecture.ipynb` — analysis of spatial immune architecture.
- `09_spatial_immunosenescence.ipynb` — spatial analysis of immunosenescence signatures.
- `10_spatial_niche_discovery.ipynb` — discovery of spatial niches.
- `12_spatial_niche_ccc.ipynb` — cell-cell communication analysis in spatial niches.

### Cell-cell communication
- `11_sc_ccc.ipynb` — cell-cell communication analysis in the single-cell data.

## Notes

The notebooks in `scr/` are intended to be run in sequence, with each stage building on the results of the previous one.
