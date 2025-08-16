### **Sources and Collection Methods**

* **Primary Data Sources:**

  * **Fermi Gamma-ray Burst Monitor (GBM) Catalogue** (2008–2018)

    * Reference: von Kienlin et al. (2020); Poolakkil et al. (2021).
    * Includes 2,356 detected GRBs; 135 with known redshift.
  * **Konus-Wind (KW) Catalogue** (2005–2018)

    * Reference: Tsvetkova et al. (2021).
    * GRB sample with measured redshifts.
  * Data obtained from:

    * [Fermi GBM Burst Catalog at HEASARC](https://heasarc.gsfc.nasa.gov/W3Browse/fermi/fermigbrst.html)
    * [Fermi GBM data tools](https://fermi.gsfc.nasa.gov/ssc/data/analysis/gbm/)
    * [Konus-Wind GRB repository](http://www.ioffe.ru/LEA/zGRBs/part2/index.html).

* **Collection:**
  Spectral parameters were derived from time-resolved fits of GRB prompt emission spectra using **Band** and **Comptonized (Comp)** models. Spectral fits cover:

  * GBM: 8–1000 keV
  * KW: 80–1200 keV

---

### **Features / Variables**

From **Table 1**:

* **Common parameters:**

  * **T90**: burst duration (time over which 90% of the flux is observed).
  * **P\_bolo**: bolometric peak flux.
  * **S\_bolo**: bolometric fluence.

* **Spectral fitting parameters:**

  * **Band model:**

    * α (low-energy photon index),
    * β (high-energy photon index),
    * E\_p (spectral peak energy).
  * **Comptonized model:**

    * α (photon index),
    * E\_p (spectral peak energy).

* **Feature sets used:**

  * **Peak flux parameters:** (α, β/Ep, P\_bolo).
  * **Fluence parameters:** (α, β/Ep, S\_bolo).
  * Both flux and fluence used separately and combined.

* **Target variable:** Redshift (*z*) of the GRB.

---

### **Sample Size**

After selection and cleaning:

* **Training/Testing Data (with known z):**

  * GBM: **122 LGRBs** (13 SGRBs excluded).
  * KW: **338 LGRBs**.
  * Total used for training/testing: **\~460 GRBs**.

* **Prediction Dataset (without z):**

  * GBM:

    * \~1708 GRBs (Comp flux model).
    * 647–1858 GRBs depending on spectral model.

---

### **Preprocessing Steps**

1. **Logarithmic Transformation**: Applied to variables T90, Ep, S\_bolo, and P\_bolo.
2. **Standardization (Z-score normalization):** Ensured zero mean and unit variance across features.
3. **Filtering Criteria:**

   * Removed GRBs with >100% uncertainty in spectral parameters.
   * Removed GRBs lacking Ep values across all models.
   * Excluded Band-fitted GRBs with β ≥ −2 (indicating no spectral peak).
   * Excluded short GRBs (SGRBs) to focus on long GRBs (LGRBs).
4. **Separate datasets** prepared for **Band**, **Comptonized**, and combined models.

---

### **Application in the Study**

* Dataset used to **train Deep Neural Networks (DNNs)** with regression setup, targeting redshift prediction.
* Predictions were combined in a **stacking ensemble** with Random Forest as the meta-learner.
* Applied to GBM GRBs without measured z to estimate pseudo-redshifts.
* Validated against **Amati** and **Yonetoku** correlations to check astrophysical consistency.

---

### **Limitations**

* **Small training sample:** Only \~460 GRBs with spectroscopic redshifts available.
* **Selection bias:** Redshift measurements require optical follow-up, favoring brighter or closer bursts.
* **Spectral model dependence:** Band vs. Compton fits can yield different parameter estimates.
* **Energy coverage mismatch:** GBM (8–1000 keV) vs. KW (80–1200 keV).
* **Excluded data:** GRBs with large parameter errors or missing spectral peak information.
* **Range limitations:** Model predictions more reliable within z ≈ 0.5–6, reflecting training sample distribution.

---

✅ In summary:
The dataset consisted of **Fermi-GBM (2008–2018) and Konus-Wind (2005–2018) GRBs with known redshifts (\~460 bursts)**, curated using strict selection criteria and spectral fitting (Band/Comptonized). Features included duration, spectral parameters, flux, and fluence. Preprocessing involved log transformation, standardization, and error-based filtering. This curated dataset trained DNN + Random Forest ensemble models to estimate redshift for **>1700 GRBs without measured z**, later validated against astrophysical correlations.


Here’s a **structured summary table** of the dataset used in *Aldowma & Razzaque (2024)*:

---

### 📊 Dataset Summary – GRB Redshift Estimation

| **Aspect**                         | **Details**                                                                                                                                                                                                                                                                                               |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sources**                        | - **Fermi Gamma-ray Burst Monitor (GBM)** (2008–2018)  <br> - **Konus-Wind (KW)** (2005–2018)                                                                                                                                                                                                             |
| **Access**                         | - [Fermi GBM Catalog](https://heasarc.gsfc.nasa.gov/W3Browse/fermi/fermigbrst.html)  <br> - [Fermi GBM Tools](https://fermi.gsfc.nasa.gov/ssc/data/analysis/gbm/)  <br> - [Konus-Wind GRB Repository](http://www.ioffe.ru/LEA/zGRBs/part2/index.html)                                                     |
| **Collection Method**              | Prompt gamma-ray emission spectra fitted with **Band** and **Comptonized** models. Energy ranges: <br> - GBM: 8–1000 keV <br> - KW: 80–1200 keV                                                                                                                                                           |
| **Sample Size (Training/Testing)** | - GBM: **122 LGRBs** (135 with z, 13 SGRBs excluded) <br> - KW: **338 LGRBs** <br> - **Total with redshift ≈ 460**                                                                                                                                                                                        |
| **Prediction Dataset (No z)**      | - GBM: 647–1858 GRBs depending on model <br> - Best-fit model applied to **1708 GRBs** for pseudo-redshift estimation                                                                                                                                                                                     |
| **Features / Variables**           | - **Common:** T90 (burst duration), P\_bolo (bolometric peak flux), S\_bolo (bolometric fluence) <br> - **Band model:** α (low-energy index), β (high-energy index), E\_p (peak energy) <br> - **Comptonized model:** α (index), E\_p (peak energy)                                                       |
| **Target Variable**                | Redshift (*z*)                                                                                                                                                                                                                                                                                            |
| **Preprocessing**                  | - Log-transform: T90, E\_p, S\_bolo, P\_bolo <br> - Standardization (Z-score normalization) <br> - Filtering: removed GRBs with >100% parameter errors, missing E\_p, or Band β ≥ −2 <br> - Excluded short GRBs (SGRBs)                                                                                   |
| **Application**                    | - Train/test Deep Neural Networks (DNNs) with regression setup <br> - Combine outputs with **Random Forest** in stacking ensemble <br> - Apply models to GBM GRBs w/o redshift to infer pseudo-z <br> - Validate pseudo-z samples via **Amati** & **Yonetoku** correlations                               |
| **Limitations**                    | - Limited training sample (\~460 GRBs) <br> - Selection bias (redshift requires optical follow-up) <br> - Dependence on spectral model (Band vs. Comptonized) <br> - Instrument mismatch (GBM vs. KW energy ranges) <br> - Excluded GRBs with poor/missing spectral fits <br> - Reliable within z ≈ 0.5–6 |

----

# Dataset Description for "Deep Neural Networks for Estimation of Gamma-Ray Burst Redshifts"

## Overview

The dataset used in this study combines **Gamma-Ray Burst (GRB)** observations from two major space-based instruments to train machine learning models for redshift estimation. The research focuses specifically on **Long Gamma-Ray Bursts (LGRBs)** with well-measured spectral parameters and known redshifts.[1][2]

## Data Sources

### Primary Instruments

**Fermi Gamma-ray Burst Monitor (Fermi-GBM)**
- **Sample Size**: 127 LGRBs with measured redshift information[1]
- **Energy Range**: 8-1000 keV for spectral fitting[1]
- **Time Period**: Data spans from 2008 to at least 2022[3]
- **Total GBM Catalog**: Contains more than 3,000 events, with approximately 16% classified as Short GRBs[1]

**Konus-Wind (KW)**
- **Sample Size**: 338 LGRBs with measured redshift information[1]
- **Energy Range**: 80-1200 keV for spectral fitting[1]
- **Time Period**: 2005 to 2018[1]
- **Detector Configuration**: Two identical detectors (S1 and S2) with response functions calculated for 5 keV - 10 MeV[4]

### Combined Training Dataset
- **Total Training Sample**: 465 LGRBs (127 from GBM + 338 from KW)[1]
- **Redshift Range**: Up to z = 8.2[1]
- **Quality Criteria**: All bursts have well-measured prompt gamma-ray flux and spectral information[2][1]

## Dataset Features and Variables

### Spectral Parameters

The study utilizes spectral fitting parameters obtained from two primary spectral models:[1]

**Band Model Parameters**:[5][6]
- Low-energy photon index (α)
- High-energy photon index (β) 
- Peak energy (E_peak) in the νFν spectrum
- Amplitude/normalization factor

**Comptonized Model Parameters**:[6][5]
- Power-law index
- Peak energy (E_peak)
- Exponential cutoff energy
- Flux normalization

### Observable Quantities

**Temporal Characteristics**:
- **T₉₀**: Duration of the burst (time interval containing 90% of the burst fluence)[1]
- **Peak flux interval**: Time range of maximum gamma-ray emission[1]

**Spectral Flux Measurements**:
- **Peak bolometric flux**: Maximum gamma-ray flux during the burst[1]
- **Fluence**: Total energy flux integrated over the burst duration[1]
- **Energy fluence**: Measured in specific energy bands (e.g., 50-300 keV)[6]

**Physical Parameters** (calculated from spectral fits):
- **E_{i,p}**: Peak photon energy in the cosmological rest frame[2][1]
- **E_{iso}**: Isotropic-equivalent radiated energy during prompt phase[2][1]
- **L_{iso}**: Isotropic-equivalent luminosity during peak flux interval[2][1]

## Data Collection and Processing Methods

### Spectral Fitting Procedures

**Fermi-GBM Analysis**:[6]
- Uses rmfit software (version 3.3pr7 or later)
- Combines multiple detectors (NaI and BGO) for improved statistics
- Detector selection based on illumination angle ( ≤ 60° typically)

**Exclusion Criteria**:
- Short Gamma-Ray Bursts (SGRBs) removed from analysis[1]
- Bursts without adequate spectral fitting quality
- GRBs lacking redshift measurements

## Preprocessing Steps

### Spectral Model Selection
The study employs **ensemble stacking methods** combining Deep Neural Networks with Random Forest algorithms. Different spectral fitting approaches are tested:[1]

- **Band fluence**: Using Band model parameters from fluence measurements  
- **Band flux**: Using Band model parameters from peak flux measurements  
- **Comp fluence**: Using Comptonized model parameters from fluence measurements  
- **Comp flux**: Using Comptonized model parameters from peak flux measurements  
- **Combined models**: Using both fluence and flux parameters together[1]

### Data Validation
- **Model Performance Metrics**: R² coefficient and Mean Absolute Error (MAE) for goodness of fit[1]
- **Statistical Testing**: Two-sided Kolmogorov-Smirnov tests comparing pseudo-redshift and true redshift distributions[1]
- **Cross-validation**: Separate training and test datasets with 95% confidence intervals using bootstrapped methods[1]

## Dataset Limitations

### Sample Size Constraints
- **Limited Redshift Sample**: The authors acknowledge working with a "limited number of available predictors" - specifically 126 GBM LGRBs and 338 KW LGRBs with known redshift[1]
- **Spectral Information Gaps**: Not all spectral information is available for each GRB, leading to varying sample sizes across different model applications[1]

### Instrumental Biases
- **Energy Range Limitations**: Different energy windows between instruments (GBM: 8-1000 keV vs KW: 80-1200 keV) may introduce systematic effects[1]
- **Detection Bias**: Higher energy thresholds may preferentially select intrinsically brighter or closer bursts[8]
- **Spectral Model Dependencies**: Results may vary depending on choice between Band and Comptonized fitting functions[1]

### Temporal Coverage
- **Data Span Limitations**: KW data limited to 2005-2018 period[1]
- **Evolving Instrumental Capabilities**: Different detection sensitivities and analysis methods across the observation periods

### Redshift Distribution
- **High-z Limitations**: While GRBs are observed up to z = 8.2, the majority of the training sample likely concentrates at lower redshifts[1]
- **Selection Effects**: The requirement for spectroscopic redshift confirmation may bias toward brighter, more easily followed-up events

## Data Application in the Study

The curated dataset enables training of machine learning models to predict "pseudo-redshifts" for GRBs without known redshift measurements. The best-performing models achieve statistical consistency with true redshift distributions (p-values > 0.05 in Kolmogorov-Smirnov tests) and successfully reproduce key astrophysical correlations like the Amati and Yonetoku relations.[2][1]

The comprehensive spectral parameter database provides a foundation for advancing GRB cosmological applications, potentially enabling the use of gamma-ray bursts as standard candles for cosmological distance measurements.[2][1]

---

[1] https://academic.oup.com/mnras/article/529/3/2676/7611713  
[2] https://arxiv.org/abs/2401.11005  
[3] https://fermi.gsfc.nasa.gov/science/mtgs/symposia/eleventh/program/posters/Tamador_Fermi_sympoPoster.pdf  
[4] http://www.ioffe.ru/LEA/shortGRBs/Catalog/Data/catalog_shortGRBs_text.pdf  
[5] https://www.aanda.org/articles/aa/full_html/2011/06/aa16270-10/aa16270-10.html  
[6] https://heasarc.gsfc.nasa.gov/W3Browse/fermi/fermigbrst.html  
[7] https://ipn3.ssl.berkeley.edu/Svinkin_2016_ApJS_224_10.pdf  
[8] https://academic.oup.com/pasj/article/71/4/76/5510582  
[9] https://arxiv.org/html/2408.13598v1  
[10] https://ml4physicalsciences.github.io/2023/files/NeurIPS_ML4PS_2023_116.pdf  
[11] https://www.aanda.org/articles/aa/full_html/2025/06/aa52651-24/aa52651-24.html  
[12] https://www.bohrium.com/paper-details/grb-redshift-classifier-to-follow-up-high-redshift-grbs-using-supervised-machine-learning/1137431046334185552-514  
[13] https://indico.global/event/13394/contributions/118618/  
[14] https://academic.oup.com/mnras/article/527/2/4272/7371653  
[15] https://ui.adsabs.harvard.edu/abs/2024MNRAS.529.2676A/abstract  
[16] https://inspirehep.net/literature/2750303  
[17] https://www.aanda.org/articles/aa/full_html/2016/04/aa27509-15/aa27509-15.html  
[18] https://www.aanda.org/articles/aa/full_html/2020/12/aa37915-20/aa37915-20.html  
[19] https://www.aanda.org/articles/aa/pdf/2025/06/aa52651-24.pdf  
[20] https://fermi.gsfc.nasa.gov/ssc/data/analysis/gbm/gbm_data_tools/gdt-docs/api/api-spectra.html  
[21] https://arxiv.org/html/2410.13985v1  

