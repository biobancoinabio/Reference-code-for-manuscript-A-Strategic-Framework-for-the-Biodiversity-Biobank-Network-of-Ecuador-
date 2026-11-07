# Biodiversity Biobank Network of Ecuador — Data & Code Reproducibility

[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![License: CC BY 4.0](https://img.shields.io/badge/Data_License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![License: MIT](https://img.shields.io/badge/Code_License-MIT-green.svg)](https://opensource.org/licenses/MIT)

This repository contains the supplementary data tables, Python reproduction code, and high-resolution figures for the manuscript:

> **Consolidating a National Treasure: A Strategic Framework for the Biodiversity Biobank Network of Ecuador**  
> *Manuscript submitted for publication (2026).*

---

## Overview

This repository provides open, fully reproducible programmatic workflows for:
1. **The Latin American Biodiversity–Biobanking Paradox:** An empirical cross-national analysis evaluating threatened species vulnerability (IUCN Red List Version 2026-1 via API v4, with longitudinal comparison to the 2020-1 baseline) against domestic repository stewardship of digitized physical specimens and genomic material samples in the Global Biodiversity Information Facility (GBIF REST API v1) across 11 Latin American countries.
2. **National Biobank Capacity Mapping:** Baseline physical collection holdings and active open digital mobilization metrics across the eight member institutions of the National Biobank Network of Ecuador (*Red Nacional de Biobancos*).

---

## Repository Contents

```
├── Supplementary_Code_S1_Generate_Figures.py     # Main Python reproduction engine (APIs + figure generator)
├── Supplementary_Data_Table_S1.csv               # 11-country dataset (IUCN 2026-1/2020-1 + GBIF stewardship)
├── Supplementary_Data_Table_S2_Ecuador_Nodes_GBIF.csv # 8 Ecuadorian biobank nodes (holdings + GBIF UUIDs)
├── Supplementary_Data_Table_S3_IUCN_GBIF_key.csv # Methodological data dictionary & API query key
├── 2020_1_RL_Stats_Table_5.pdf                   # Official historical IUCN 2020-1 Table 5 reference document
└── README.md                                     # This documentation file
```

### Supplementary Files Description

| File | Description |
| :--- | :--- |
| **`Supplementary_Code_S1_Generate_Figures.py`** | Standalone Python script that queries the live GBIF REST API and IUCN Red List API v4, exports Supplementary Tables S1 and S2, and deterministically generates Figures 1–4. |
| **`Supplementary_Data_Table_S1.csv`** | Empirical dataset across 11 Latin American countries (`CO`, `BR`, `EC`, `MX`, `PE`, `VE`, `AR`, `CR`, `CL`, `CU`, `UY`) reporting land area, comprehensively assessed vertebrates (`M+B+A`), partially assessed groups (plants, fishes, reptiles, inverts, fungi), threat categories (`CR`, `EN`, `VU`), threat densities, and GBIF specimen/sample stewardship metrics. |
| **`Supplementary_Data_Table_S2_Ecuador_Nodes_GBIF.csv`** | Institutional baseline for the 8 network nodes (INABIO, INIAP, UTPL, GSC-USFQ, ESPE, CENAIM-ESPOL, Yachay Tech, Ikiam), detailing physical holdings, official GBIF publishing organization UUIDs, and live published occurrence counts. |
| **`Supplementary_Data_Table_S3_IUCN_GBIF_key.csv`** | Comprehensive data dictionary defining every variable across Tables S1 and S2, with exact API endpoints, JSON response paths, mathematical formulas for derived indicators (`dom_spec_pct`, `dom_combined_pct`), and validation rules. |

---

## Installation & Requirements

The reproduction workflow requires **Python 3.9+** and standard scientific libraries (`numpy`, `matplotlib`). All network operations use the Python standard library (`urllib`, `json`, `csv`).

```bash
# Clone the repository
git clone https://github.com/your-username/ecuador-biobank-network.git
cd ecuador-biobank-network

# Install minimal dependencies
pip install numpy matplotlib
```

---

## Quickstart & Reproducibility

### 1. Deterministic Figure & Table Generation (Offline / Verified Snapshot)
To reproduce all four publication figures and export Tables S1 and S2 using the verified API snapshot:
```bash
python Supplementary_Code_S1_Generate_Figures.py
```
*Outputs: 300 DPI PNG and vector PDF files for Figures 1–4, and CSV files for Tables S1–S2.*

### 2. Live Query to GBIF REST API v1
To execute live HTTP queries against GBIF endpoints (`https://api.gbif.org/v1/`) without authentication:
```bash
python Supplementary_Code_S1_Generate_Figures.py --live-gbif
```

### 3. Live Query to IUCN Red List API v4
To query live country-level threatened species assessments directly from the official IUCN API v4 (`https://api.iucnredlist.org/api/v4/`):
```bash
python Supplementary_Code_S1_Generate_Figures.py --live-iucn --iucn-token YOUR_IUCN_TOKEN
```
*(An API token can be requested from the [IUCN Red List API Portal](https://api.iucnredlist.org/).)*

---

## Data Sources & Attribution

* **IUCN Red List of Threatened Species (Version 2026-1):** Country assessments extracted via IUCN API v4 and Summary Statistics Table 1a / Table 5.
* **Global Biodiversity Information Facility (GBIF):** Occurrence search, organization registry, and Global Registry of Scientific Collections (GrSciColl) accessed via the [GBIF REST API v1](https://api.gbif.org/v1/).
* **Institutional Records:** Public institutional annual reports, collection registries, and direct institutional engagement across the National Biobank Network of Ecuador (INABIO, INIAP, UTPL, USFQ, ESPE, CENAIM-ESPOL, Yachay Tech, and Ikiam).

---

## License

* **Code:** The Python script (`Supplementary_Code_S1_Generate_Figures.py`) is distributed under the [MIT License](https://opensource.org/licenses/MIT).
* **Data & Figures:** The supplementary data tables and figures are distributed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
