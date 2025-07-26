# GRB-ML

This project uses Machine Learning to analyze Gamma-ray bursts (GRBs) as potential cosmological standard candles, focusing on improving their standardization and refining empirical relations like the Amati and Yonetoku relations. By exploring correlations between observable quantities and derived cosmological parameters, we aim to constrain the Hubble constant and dark energy density. The goal is to enhance redshift calculations and contribute to understanding the universe's expansion.


#### 1. CONTEXT

Astrophysical data is expanding at an unprecedented rate as modern telescopes and detectors continue to evolve. Traditional methods struggle to keep pace with the growing data volumes, often missing subtle patterns and rare events. Manual classification is both time-consuming and prone to errors. However, this presents a significant opportunity. Machine Learning (ML) is rapidly becoming the tool of choice for analyzing astrophysical data, acting as the "telescope" of the 21st century.

##### Why Machine Learning?

- **Process Unprecedented Data Volumes**: From gigabytes to exabytes, ML scales with the universe's complexity, handling massive datasets efficiently.
- **Identify Hidden Patterns**: ML enables the discovery of anomalies, classification of celestial objects, and the detection of faint signals invisible to the human eye.
- **Accelerate Discovery**: By automating repetitive tasks, ML frees astronomers to focus on more complex analyses and theoretical advancements.
- **Uncover New Physics**: ML can reveal previously undetectable relationships and structures, paving the way for groundbreaking theories.


##### A. Cosmological Standard Candles

In cosmology, "standard candles" are astronomical objects with a known intrinsic brightness. This predictable luminosity allows astronomers to measure distances in the universe using the inverse-square law of light. Standard candles play a key role in constructing the "cosmic distance ladder," which helps determine the scale of the universe and its expansion. Examples include Cepheid variables and Type Ia supernovae.

##### B. Type Ia Supernovae

Although Type Ia supernovae are valuable standard candles, they are not perfect. Variations in their peak brightness and light curves exist, but the Phillips Relation helps standardize them. This relation shows that brighter supernovae tend to decline more slowly, and by observing their light curve, astronomers can apply corrections to refine their luminosity estimates.

##### C. Gamma-Ray Bursts (GRBs)

Gamma-ray bursts (GRBs) are the most powerful explosions in the universe, capable of being detected in multiple electromagnetic wavebands. They offer a potential alternative to Type Ia supernovae as cosmological standard candles due to their ability to be detected at greater redshifts. By studying GRBs, we can help constrain cosmological parameters such as the Hubble constant and dark energy density.

Despite their promise, GRBs aren't perfect standard candles. However, empirical relations like the **Amati Relation** (relating total energy release to peak-energy in the gamma-ray spectrum) and the **Yonetoku Relation** (relating peak luminosity to peak-energy) have been proposed. These relations link observable quantities to cosmologically dependent parameters, providing a means to constrain cosmological models.


##### Objectives

While the existing empirical relations for GRBs are useful, there is a need for more accurate and "tight" relations that can provide better standardization. Machine Learning can help identify these tighter relations and further probe cosmological models. The specific tasks are as follows:

- **Explore Correlations**: Use ML techniques to uncover deeper correlations between observable quantities and cosmological parameters, standardizing GRBs as cosmological candles.
- **Constrain Cosmological Parameters**: Using the correlations found, ML can help constrain key cosmological parameters, including the Hubble constant and dark energy density.

*This repository serves as a starting point for using Machine Learning to improve the standardization of GRBs as cosmological probes, ultimately contributing to a better understanding of the universe's expansion and the cosmic distance ladder.* 
