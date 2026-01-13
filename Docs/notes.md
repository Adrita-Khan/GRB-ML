'Redshift', 'T90', 'Alpha', 'Beta', 'Ep', 'Sbolo', these are the **column names** of the dataset, and they represent different features (variables) in the data that are used for the machine learning task (in this case, predicting **Redshift**). 

* **Redshift**: This is the target variable in the dataset. In astronomy, redshift refers to the increase in wavelength (or decrease in frequency) of electromagnetic radiation emitted by an object moving away from the observer. It is commonly used to measure the velocity at which an astronomical object is receding due to the expansion of the universe. In this context, the model aims to predict the redshift based on other features.

* **T90**: This represents the duration of a gamma-ray burst (GRB) during which 90% of the total observed counts are detected. It is a measure of the burst's duration and is often used to classify GRBs into short and long categories.

* **Alpha (α)**: This is the spectral index of the low-energy part of the GRB's spectrum. It characterizes the energy distribution of the emitted radiation in the lower energy range.

* **Beta (β)**: This is the spectral index of the high-energy part of the GRB's spectrum. Similar to Alpha, it characterizes the energy distribution in the higher energy range.

* **Ep**: This denotes the peak energy of the GRB spectrum. It is the energy at which the spectrum reaches its maximum.

* **Sbolo**: This represents the bolometric fluence of the GRB, which is the total energy emitted across all wavelengths. It is an important parameter for understanding the energy output of the burst.

These features are selected because they are believed to have predictive power regarding the redshift of GRBs. The dataset is processed by applying a base-10 logarithmic transformation to the `T90`, `Ep`, and `Sbolo` columns, while the `Alpha` and `Beta` columns are retained without transformation. This preprocessing step is common in machine learning to normalize data and make it more suitable for modeling.

