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


