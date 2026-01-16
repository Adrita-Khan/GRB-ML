# Machine Learning Applications for Gamma-Ray Burst Analysis

## Research Papers and Tools

| # | Paper Title | Year | arXiv/DOI | GitHub | Dataset | Size |
|---|-------------|------|-----------|--------|---------|------|
| 1 | GRB Redshift Estimation using Machine Learning and the Associated Web-App | 2024 | [arXiv:2410.13985](https://arxiv.org/abs/2410.13985) | [GRB-Web-App](https://github.com/gammarayapp/GRB-Web-App) | Swift BAT/XRT | 238 training, 276 predicted |
| 2 | GRB Redshift Classifier to Follow-up High-Redshift GRBs | 2024 | [arXiv:2408.08763](https://arxiv.org/abs/2408.08763) | [Redshift-Classifier](https://github.com/Milind018/Redshift-Classifier) | Swift XRT Plateau | 251 GRBs |
| 3 | Deep Neural Networks for Estimation of Gamma-Ray Burst Redshifts | 2024 | [arXiv:2401.11005](https://arxiv.org/abs/2401.11005) | Not available | Fermi-GBM + Konus-Wind | 1,576 pseudo-z GRBs |
| 4 | Machine-z: Rapid Machine Learned Redshift Indicator for Swift GRBs | 2016 | [arXiv:1512.07671](https://arxiv.org/abs/1512.07671) | Not available | Swift BAT/XRT/UVOT | 284 GRBs |
| 5 | New Results in Applying Machine Learning to GRB Redshift Estimation | 2017-2023 | [PoS 312/079](https://pos.sissa.it/312/079/) | Not available | Swift BAT/XRT/UVOT | 328-400 GRBs |
| 6 | Reconstructing the Hubble Diagram of Gamma-Ray Bursts Using Deep Learning | 2021 | [arXiv:2111.10052](https://arxiv.org/abs/2111.10052) | Not available | GRB Combo-relation + Pantheon SNe Ia | 174 GRBs |
| 7 | Redshift Classification of Optical Gamma-Ray Bursts using Supervised Learning | 2024 | [arXiv:2512.13038](https://arxiv.org/abs/2512.13038) | Web app (TBA) | Swift UVOT + Ground-based | 171 GRBs, 64,813 obs |
| 8 | An Optical Gamma-Ray Burst Catalogue with Measured Redshift | 2024 | [arXiv:2405.02263](https://arxiv.org/abs/2405.02263) | [grbLC.com](http://www.grbLC.com) | Optical photometry | 535 GRBs, 64,813 obs |
| 9 | ClassiPyGRB: Machine Learning Classification | 2023 | [GitHub](https://github.com/KenethGarcia/ClassiPyGRB) | [ClassiPyGRB](https://github.com/KenethGarcia/ClassiPyGRB) | Swift BAT GRB catalog | — |
| 10 | DeepGRB: Deep Learning Detection Framework | 2024 | [GitHub](https://github.com/rcrupi/DeepGRB) | [DeepGRB](https://github.com/rcrupi/DeepGRB) | Fermi-GBM + Swift | — |
| 11 | Dark GRBs Analysis | 2020+ | [GitHub](https://github.com/cgobat/dark-GRBs) | [dark-GRBs](https://github.com/cgobat/dark-GRBs) | Optically-dark short GRBs | Custom dataset |
| 12 | GRB-ML: Physical Origin Classification | 2024 | [GitHub](https://github.com/Rigel7/grb-ml) | [grb-ml](https://github.com/Rigel7/grb-ml) | Multi-mission GRB data | Various catalogs |
| 13 | Swift GRB Parameter Estimation | 2020+ | [GitHub](https://github.com/PBGraff/SwiftGRB_PEanalysis) | [SwiftGRB_PEanalysis](https://github.com/PBGraff/SwiftGRB_PEanalysis) | Swift GRB catalog | — |

## Key Datasets

| Dataset | Description | Size/Coverage | Access Link |
|---------|-------------|---------------|-------------|
| **Swift-XRT GRB Catalogue** | Live X-ray light curves and spectral fits | Hundreds of GRBs | [Swift XRT Live Cat](https://www.swift.ac.uk/xrt_live_cat/) |
| **Swift-BAT GRB Catalogue** | Prompt gamma-ray properties | Comprehensive Swift detections | [Swift BAT Archive](https://swift.gsfc.nasa.gov/archive/grb_table/) |
| **Fermi-GBM Burst Catalog** | Spectral parameters and light curves | 3,900+ GRBs | [HEASARC Fermi-GBM](https://heasarc.gsfc.nasa.gov/W3Browse/fermi/fermigbrst.html) |
| **Aldowma Pseudo-Redshift Catalog** | ML-predicted redshifts for Fermi GRBs | 1,576 GRBs | [Zenodo Dataset](https://doi.org/10.5281/zenodo.13695954) |
| **Dainotti Optical Catalog** | Comprehensive optical light curves | 64,813 observations, 535 GRBs | [grbLC.com](http://www.grbLC.com) |
| **Konus-Wind GRB Catalog** | Spectral parameters from Konus-Wind | Extensive spectral data | [IKI GRB Database](http://www.ioffe.ru/LEA/kwgrbdb/) |
| **Pantheon SNe Ia** | Type Ia supernova cosmology sample | 1,701 SNe Ia | [PantheonPlusSH0ES](https://pantheonplussh0es.github.io/) |

## Dataset Usage by Research Focus

**Redshift Estimation**: Swift BAT/XRT/UVOT, Fermi-GBM, Konus-Wind, Dainotti Optical Catalog

**Classification Tasks**: Swift BAT, Fermi-GBM, Optical photometry

**Cosmological Studies**: GRB Combo-relation, Pantheon SNe Ia

**Dark GRB Analysis**: Swift XRT, Optical catalogs (custom compilations)
