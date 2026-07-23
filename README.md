# Cloudiness Effects on Exoplanetary Spectra Degeneracy

This repository contains the scientific pipeline, simulation grids, and statistical analysis tools used to study atmospheric degeneracy in hot Jupiters, with a specific focus on WASP-17b. The project utilizes the NASA Planetary Spectrum Generator (PSG) to model forward radiance spectra and evaluate how varying terminator cloudiness impacts the retrieval of atmospheric parameters.

---

## Scientific Context

Atmospheric characterization of exoplanets via radiance spectroscopy frequently encounters degeneracy, where distinct physical scenarios (e.g., high-altitude cloud decks versus varying chemical abundances) produce similar spectral signatures. 

Following the empirical framework of Sing et al. (2016) and other work, WASP-17b is modeled as a cloudy/hazy hot Jupiter. This project simulates transit observations using the JWST NIRISS-SOSS instrument profile ($0.8 - 2.2 μm$) to:
1. Model spatial and terminator asymmetry (ingress vs. egress) under various cloud fractions.
2. Characterize the dampening of the $1.4 μm$ water vapor ($H_2O$) absorption feature caused by Quartz condensate scattering.
3. Determine the minimum Signal-to-Noise Ratio (SNR) and observational thresholds required to break these degeneracies via automated statistical analysis - regional and global.

---

## Directory Structure

The core components of the project are organized as follows:

*   **`01_PSG_Asymmetry_Pipeline.ipynb`** — Automates API queries to NASA PSG, managing ingress, mid-transit, and egress configurations, annuling possibilities of human error during actual making of files.
*   **`02_Asymmetry_Analysis.ipynb`** — Processes raw spectral outputs, evaluates differential absorption, and extracts baseline variations.
*   **`03_SNR_and_Summary_Plots.ipynb`** — Visualizes spectral lines, trends, and instrument simulation outputs.
*   **`04_Noise_and_Detectability.ipynb`** — Introduces Gaussian instrumental noise to determine statistical significance thresholds.
*   **`05_Cfg_Parameter_Extraction.ipynb`** — Utility script for parsing and verifying PSG `.cfg` file parameters.
*   **`Statisticka-analiza-automatizovana.ipynb`** — Core statistical suite executing automated reduced Chi-squared ($χ^2$) grid searches and variance testing, doing all previous 5 files in one place.
*   **`Asym_0.1/` to `Asym_1.0/`** — Grid directories containing NASA PSG input files (`.cfg`) and simulated output spectra (`.txt`) across varying degrees of structural terminator asymmetry.
*   **`Literature_Alderson_Symmetric/` & `Literature_Alderson_Mild_Asymmetry/`** — Validation benchmarks utilizing parameters synced with standard literature data (Sing 2016, Alderson 2022).
*   **`WASP17b_primjer/`** — Manual verification sandbox and control runs for standard hot Jupiter parameters ($T_{eq} = 1770K$, $R_{p} = 1.99\ R_J$, $M_p = 0.486 M_J$), checking one example of literature case if it produces the spectrum or it has some differences in between.

---

## Methodology and Instrumentation

*   **Simulation Engine:** NASA Planetary Spectrum Generator (PSG)
*   **Instrument Profile:** JWST NIRISS-SOSS ($0.8 - 2.2\ μm$), optimizing the detection of the $1.4\ μm$ $H_2O$ band.
*   **Aerosol Model:** Quartz ($SiO_2$) condensates with a uniform grain size of $1.0\ μm$ and a variable baseline cloud fraction ($0.5$ for realistic degenerate dampening).
*   **Statistical Suite:** Python-based automated $χ^2$ grid search, standard error propagation, and residual mapping against empirical HST/WFC3 data from Sing et al. (2016).

---

## Setup and Usage

1. Clone the repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/Cloudiness-effects-on-exoplanetary-spectra-degeneracy.git](https://github.com/YOUR_USERNAME/Cloudiness-effects-on-exoplanetary-spectra-degeneracy.git)
