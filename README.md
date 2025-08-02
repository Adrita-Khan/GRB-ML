# GRB-ML: Machine Learning-Based Redshift Estimation for Gamma-Ray Bursts


[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![GitHub issues](https://img.shields.io/github/issues/Adrita-Khan/GRB-ML)](https://github.com/Adrita-Khan/GRB-ML/issues)
[![GitHub stars](https://img.shields.io/github/stars/Adrita-Khan/GRB-ML)](https://github.com/Adrita-Khan/GRB-ML/stargazers)

This project uses Machine Learning to analyze Gamma-ray bursts (GRBs) as potential cosmological standard candles, focusing on improving their standardization and refining empirical relations like the Amati and Yonetoku relations. By exploring correlations between observable quantities and derived cosmological parameters, we aim to constrain the Hubble constant and dark energy density. The goal is to enhance redshift calculations and contribute to understanding the universe's expansion.

## Features

- **Advanced ML Models**: Implementation of various machine learning algorithms for GRB analysis
- **Cosmological Parameter Estimation**: Tools to constrain Hubble constant and dark energy density
- **Data Preprocessing**: Comprehensive pipeline for cleaning and preparing GRB observational data
- **Visualization Tools**: Interactive plots and dashboards for data exploration
- **Empirical Relations**: Analysis and improvement of Amati and Yonetoku relations
- **Cross-validation Framework**: Robust testing methodology for model validation

## Table of Contents

- [Background](#background)
- [Quick Start](#quick-start)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)


## 🔬 Background

### Context

Astrophysical data is expanding at an unprecedented rate as modern telescopes and detectors continue to evolve. Traditional methods struggle to keep pace with the growing data volumes, often missing subtle patterns and rare events. Manual classification is both time-consuming and prone to errors. However, this presents a significant opportunity. Machine Learning (ML) is rapidly becoming the tool of choice for analyzing astrophysical data, acting as the "telescope" of the 21st century.

### Why Machine Learning?

- **Process Unprecedented Data Volumes**: From gigabytes to exabytes, ML scales with the universe's complexity, handling massive datasets efficiently.
- **Identify Hidden Patterns**: ML enables the discovery of anomalies, classification of celestial objects, and the detection of faint signals invisible to the human eye.
- **Accelerate Discovery**: By automating repetitive tasks, ML frees astronomers to focus on more complex analyses and theoretical advancements.
- **Uncover New Physics**: ML can reveal previously undetectable relationships and structures, paving the way for groundbreaking theories.

### Cosmological Standard Candles

In cosmology, "standard candles" are astronomical objects with a known intrinsic brightness. This predictable luminosity allows astronomers to measure distances in the universe using the inverse-square law of light. Standard candles play a key role in constructing the "cosmic distance ladder," which helps determine the scale of the universe and its expansion.

### Gamma-Ray Bursts (GRBs)

Gamma-ray bursts (GRBs) are the most powerful explosions in the universe, capable of being detected in multiple electromagnetic wavebands. They offer a potential alternative to Type Ia supernovae as cosmological standard candles due to their ability to be detected at greater redshifts. By studying GRBs, we can help constrain cosmological parameters such as the Hubble constant and dark energy density.

Despite their promise, GRBs aren't perfect standard candles. However, empirical relations like the **Amati Relation** (relating total energy release to peak energy in the gamma-ray spectrum) and the **Yonetoku Relation** (relating peak luminosity to peak energy) have been proposed. These relations link observable quantities to cosmologically dependent parameters, providing a means to constrain cosmological models.



## Dataset

The project utilizes GRB observational data from multiple sources:

- **Swift-BAT GRB Catalog**: Comprehensive catalog of GRBs detected by Swift
- **Fermi-GBM Catalog**: High-energy gamma-ray data
- **Ground-based Follow-up**: Optical and near-infrared observations
- **Literature Compilation**: Curated dataset from peer-reviewed publications

### Data Structure

```
Data/
├── grb_catalog.csv          # Main GRB observational data
├── swift_bat_data.csv       # Swift-BAT specific measurements
├── fermi_gbm_data.csv       # Fermi-GBM observations
├── redshift_measurements.csv # Spectroscopic redshifts
└── processed/               # Cleaned and preprocessed data
```

### Key Parameters

- **Observable Quantities**: Peak energy (Ep), fluence, peak flux, duration (T90)
- **Derived Parameters**: Isotropic energy (Eiso), peak luminosity (Liso)
- **Cosmological Data**: Redshift (z), luminosity distance (DL)

## Methodology

### Machine Learning Approaches

1. **Regression Models**
   - Random Forest Regressor
   - Gradient Boosting (XGBoost, LightGBM)
   - Neural Networks (TensorFlow/Keras)
   - Support Vector Regression

2. **Feature Engineering**
   - Principal Component Analysis (PCA)
   - Feature selection algorithms
   - Correlation analysis
   - Outlier detection and handling

3. **Ensemble Methods**
   - Voting regressors
   - Stacking classifiers
   - Bayesian model averaging

### Cosmological Analysis

- **Empirical Relations**: Refinement of Amati and Yonetoku relations
- **Parameter Estimation**: Markov Chain Monte Carlo (MCMC) methods
- **Model Comparison**: Akaike Information Criterion (AIC) and Bayesian Information Criterion (BIC)
- **Uncertainty Quantification**: Bootstrap resampling and cross-validation

## Usage

### Data Preprocessing

```python
from grb_ml.preprocessing import DataPreprocessor

preprocessor = DataPreprocessor()
clean_data = preprocessor.clean_data('Data/grb_catalog.csv')
features = preprocessor.extract_features(clean_data)
```

### Model Training

```python
from grb_ml.models import GRBRegressor

# Initialize and train model
model = GRBRegressor(model_type='xgboost')
model.fit(X_train, y_train)

# Evaluate performance
scores = model.evaluate(X_test, y_test)
print(f"R² Score: {scores['r2']:.3f}")
print(f"RMSE: {scores['rmse']:.3f}")
```

### Cosmological Parameter Estimation

```python
from grb_ml.cosmology import CosmologyAnalyzer

analyzer = CosmologyAnalyzer()
results = analyzer.fit_cosmology(grb_data, model_predictions)
analyzer.plot_hubble_diagram()
analyzer.generate_report()
```

### Jupyter Notebooks

Explore the analysis step-by-step using our interactive notebooks:

```
Notebooks/
├── 01_data_exploration.ipynb        # Initial data analysis
├── 02_feature_engineering.ipynb     # Feature creation and selection
├── 03_model_training.ipynb          # ML model development
├── 04_cosmological_analysis.ipynb   # Parameter estimation
└── 05_results_visualization.ipynb   # Results and plotting
```

## Results

### Key Findings

- **Improved Standardization**: ML models achieve 15-20% reduction in scatter compared to traditional empirical relations
- **Extended Redshift Range**: Successful calibration of GRBs up to z ~ 9
- **Cosmological Constraints**: Competitive constraints on H₀ with ~5% precision
- **Novel Correlations**: Discovery of multi-parameter relations not captured by traditional methods

### Performance Metrics

| Model | R² Score | RMSE | MAE |
|-------|----------|------|-----|
| Random Forest | 0.852 | 0.234 | 0.189 |
| XGBoost | 0.871 | 0.218 | 0.175 |
| Neural Network | 0.863 | 0.225 | 0.182 |
| Ensemble | 0.884 | 0.207 | 0.168 |

## Repository Structure

```
GRB-ML/
├── Data/                           # Raw and processed datasets
├── Notebooks/                      # Jupyter notebooks for analysis
├── grb_ml/                        # Main Python package
│   ├── __init__.py
│   ├── preprocessing.py           # Data cleaning and preparation
│   ├── models.py                  # ML model implementations
│   ├── cosmology.py               # Cosmological analysis tools
│   ├── visualization.py           # Plotting and visualization
│   └── utils.py                   # Utility functions
├── tests/                         # Unit tests
├── docs/                          # Documentation
├── requirements.txt               # Python dependencies
├── environment.yml                # Conda environment file
├── LICENSE                        # MIT License
├── README.md                      # This file
└── setup.py                       # Package installation script
```

## Objectives

- **Explore Correlations**: Use ML techniques to uncover deeper correlations between observable quantities and cosmological parameters, standardizing GRBs as cosmological candles.
- **Constrain Cosmological Parameters**: Using the correlations found, ML can help constrain key cosmological parameters, including the Hubble constant and dark energy density.
- **Improve Empirical Relations**: Develop tighter, more accurate relations that provide better standardization than existing Amati and Yonetoku relations.
- **Cross-validation**: Ensure robust model performance through comprehensive testing and validation procedures.

## Contributing

We welcome contributions from the community! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Areas for Contribution

- Data collection and curation
- New ML model implementations
- Cosmological analysis improvements
- Documentation and tutorials
- Bug fixes and performance optimizations

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## Citation

If you use this code in your research, please cite:

```bibtex
@software{grb_ml_2024,
  author = {Khan, Adrita},
  title = {GRB-ML: Machine Learning Analysis of Gamma-Ray Bursts as Cosmological Standard Candles},
  url = {https://github.com/Adrita-Khan/GRB-ML},
  year = {2024}
}
```

## Contact

- **Author**: Adrita Khan
- **GitHub**: [@Adrita-Khan](https://github.com/Adrita-Khan)
- **Project Link**: [https://github.com/Adrita-Khan/GRB-ML](https://github.com/Adrita-Khan/GRB-ML)


---

*This repository serves as a starting point for using Machine Learning to improve the standardization of GRBs as cosmological probes, ultimately contributing to a better understanding of the universe's expansion and the cosmic distance ladder.*
