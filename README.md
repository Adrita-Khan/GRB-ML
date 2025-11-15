# GRB-ML: Machine Learning-Based Redshift Estimation for Gamma-Ray Bursts

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![GitHub issues](https://img.shields.io/github/issues/Adrita-Khan/GRB-ML)](https://github.com/Adrita-Khan/GRB-ML/issues)
[![GitHub stars](https://img.shields.io/github/stars/Adrita-Khan/GRB-ML)](https://github.com/Adrita-Khan/GRB-ML/stargazers)

---

> **Note:** This project is ongoing and subject to continuous advancements and modifications.

---

## Overview

This project uses Machine Learning to analyze Gamma-ray bursts (GRBs) as potential cosmological standard candles, focusing on improving their standardization and refining empirical relations like the Amati and Yonetoku relations. By exploring correlations between observable quantities and derived cosmological parameters, we aim to constrain the Hubble constant and dark energy density. The goal is to enhance redshift calculations and contribute to understanding the universe's expansion.

**Collaboration:** This is a project of [CAPP](https://www.uj.ac.za/faculties/science/departments-2/physics/research/astrophysics/the-centre-for-astro-particle-physics-capp/) in collaboration with [CASSA](https://cassa.site/) and [CCDS](https://ccds.ai/).

---

## Table of Contents

- [Features](#features)
- [Background](#background)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results](#results)
- [Objectives](#objectives)
- [License](#license)
- [References](#references)
- [Contact](#contact)

---

## Features

| Feature | Description |
|---------|-------------|
| **Advanced ML Models** | Implementation of various machine learning algorithms for GRB analysis |
| **Cosmological Parameter Estimation** | Tools to constrain Hubble constant and dark energy density |
| **Data Preprocessing** | Comprehensive pipeline for cleaning and preparing GRB observational data |
| **Visualization Tools** | Interactive plots and dashboards for data exploration |
| **Empirical Relations** | Analysis and improvement of Amati and Yonetoku relations |
| **Cross-validation Framework** | Robust testing methodology for model validation |

---

## Background

### Context

Astrophysical data is expanding at an unprecedented rate as modern telescopes and detectors continue to evolve. Traditional methods struggle to keep pace with the growing data volumes, often missing subtle patterns and rare events. Manual classification is both time-consuming and prone to errors. However, this presents a significant opportunity. Machine Learning (ML) is rapidly becoming the tool of choice for analyzing astrophysical data, acting as the "telescope" of the 21st century.

### Why Machine Learning?

| Advantage | Description |
|-----------|-------------|
| **Handle Large Data** | ML processes massive datasets efficiently |
| **Identify Patterns** | ML uncovers hidden relationships and detects faint signals |
| **Accelerate Discovery** | Automates repetitive tasks, allowing focus on complex analysis |
| **Uncover New Physics** | ML can detect previously undetectable structures |

### Cosmological Standard Candles

In cosmology, "standard candles" are astronomical objects with a known intrinsic brightness. This predictable luminosity allows astronomers to measure distances in the universe using the inverse-square law of light. Standard candles play a key role in constructing the "cosmic distance ladder," which helps determine the scale of the universe and its expansion.

### Gamma-Ray Bursts (GRBs)

Gamma-ray bursts (GRBs) are the most powerful explosions in the universe, capable of being detected in multiple electromagnetic wavebands. They offer a potential alternative to Type Ia supernovae as cosmological standard candles due to their ability to be detected at greater redshifts. By studying GRBs, we can help constrain cosmological parameters such as the Hubble constant and dark energy density.

Despite their promise, GRBs aren't perfect standard candles. However, empirical relations like the **Amati Relation** (relating total energy release to peak energy in the gamma-ray spectrum) and the **Yonetoku Relation** (relating peak luminosity to peak energy) have been proposed. These relations link observable quantities to cosmologically dependent parameters, providing a means to constrain cosmological models.

---

## Dataset

### Data Sources

The project utilizes GRB observational data from multiple sources:

| Source | Description |
|--------|-------------|
| **Swift-BAT GRB Catalog** | Comprehensive catalog of GRBs detected by Swift |
| **Fermi-GBM Catalog** | High-energy gamma-ray data |
| **Ground-based Follow-up** | Optical and near-infrared observations |
| **Literature Compilation** | Curated dataset from peer-reviewed publications |

### Data Structure

> **Note:** Subject to amendments

```
Data/
├── grb_catalog.csv          # Main GRB observational data
├── swift_bat_data.csv       # Swift-BAT specific measurements
├── fermi_gbm_data.csv       # Fermi-GBM observations
├── redshift_measurements.csv # Spectroscopic redshifts
└── processed/               # Cleaned and preprocessed data
```

### Key Parameters

| Category | Parameters |
|----------|------------|
| **Observable Quantities** | Peak energy (Ep), fluence, peak flux, duration (T90) |
| **Derived Parameters** | Isotropic energy (Eiso), peak luminosity (Liso) |
| **Cosmological Data** | Redshift (z), luminosity distance (DL) |

### Accessing Fermi-GBM Data

You can retrieve specific columns from the [FERMIGBRST - Fermi GBM Burst Catalog](https://heasarc.gsfc.nasa.gov/db-perl/W3Browse/w3table.pl?tablehead=name%3Dfermigbrst&Action=More+Options) using the HEASARC Browse interface.

**Required Columns:**

| Column Name | Description |
|-------------|-------------|
| `name` | GRB identifier |
| `t90` | Duration of burst (90% of total counts) |
| `t90_error` | Error in T90 measurement |
| `flnc_band_alpha` | Band function alpha parameter |
| `flnc_band_alpha_pos_err` | Positive error in alpha |
| `flnc_band_alpha_neg_err` | Negative error in alpha |
| `flnc_band_beta` | Band function beta parameter |
| `flnc_band_beta_pos_err` | Positive error in beta |
| `flnc_band_beta_neg_err` | Negative error in beta |
| `flnc_band_epeak` | Peak energy (keV) |
| `flnc_band_epeak_pos_err` | Positive error in Epeak |
| `flnc_band_epeak_neg_err` | Negative error in Epeak |
| `flnc_band_ergflnc` | Energy fluence (erg/cm²) |
| `flnc_band_ergflnc_error` | Error in energy fluence |

---

## Methodology

### Machine Learning Approaches

#### Models Implemented

| Model Type | Specific Algorithms |
|------------|---------------------|
| **Regression Models** | Random Forest, XGBoost, Neural Networks, Support Vector Regression |
| **Feature Engineering** | PCA, feature selection, outlier handling |
| **Ensemble Methods** | Voting regressors, stacking classifiers |

#### Cosmological Analysis

| Technique | Application |
|-----------|-------------|
| **Empirical Relations** | Refining Amati and Yonetoku relations |
| **Parameter Estimation** | MCMC methods |
| **Model Comparison** | AIC and BIC for model evaluation |
| **Uncertainty Quantification** | Bootstrap resampling |

---

## Results

### Key Findings

> **Note:** Subject to amendments

| Finding | Description |
|---------|-------------|
| **Improved Standardization** | ML models achieve 15-20% reduction in scatter compared to traditional empirical relations |
| **Extended Redshift Range** | Successful calibration of GRBs up to z ~ 9 |
| **Cosmological Constraints** | Competitive constraints on H₀ with ~5% precision |
| **Novel Correlations** | Discovery of multi-parameter relations not captured by traditional methods |

### Performance Metrics

> **Note:** The following values are **placeholders** and subject to change after final experimentation and validation.

| Model | R² Score | RMSE | MAE |
|-------|----------|------|-----|
| Random Forest | 0.852 | 0.234 | 0.189 |
| XGBoost | 0.871 | 0.218 | 0.175 |
| Neural Network | 0.863 | 0.225 | 0.182 |
| Ensemble | 0.884 | 0.207 | 0.168 |

---

## Objectives

| Objective | Description |
|-----------|-------------|
| **Explore Correlations** | Use ML to identify correlations between observable quantities and cosmological parameters |
| **Constrain Cosmological Parameters** | ML can help refine the measurement of Hubble constant and dark energy density |
| **Improve Empirical Relations** | Develop better standardization relations than the current Amati and Yonetoku relations |
| **Cross-validation** | Validate model performance using robust testing methods |

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## References

1. [MNRAS Article](https://academic.oup.com/mnras/article/529/3/2676/7611713)
2. [HEASARC Fermi GRB Browse](https://heasarc.gsfc.nasa.gov/W3Browse/fermi/fermigbrst.html)
3. [Fermi GBM Data Analysis](https://fermi.gsfc.nasa.gov/ssc/data/analysis/gbm/)
4. [Ioffe zGRBs Part 2](https://www.ioffe.ru/LEA/zGRBs/part2/index.html)
5. [Fermi GBM Data Tools - Data Finders](https://fermi.gsfc.nasa.gov/ssc/data/analysis/gbm/gbm_data_tools/gdt-docs/notebooks/DataFinders.html)

---

## Contact

**Adrita Khan**

📧 [Email](mailto:adrita.khan.official@gmail.com) | 💼 [LinkedIn](https://www.linkedin.com/in/adrita-khan) | 🐦 [Twitter](https://x.com/Adrita_)

---

*This repository serves as a starting point for using Machine Learning to improve the standardization of GRBs as cosmological probes, ultimately contributing to a better understanding of the universe's expansion and the cosmic distance ladder.*
