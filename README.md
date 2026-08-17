# Mars-ISRU-GDE-Electrolyser
"This repository contains the raw experimental data and Python code used to process mass balances and Faradaic efficiencies for the manuscript: Electrochemical CO2 reduction to CO towards Mars ISRU."

# Martian CO2 Electrolyser: In Situ Resource Utilisation (ISRU) Data Analysis

[![DOI](https://shields.io)](https://zenodo.org)
[![License: MIT](https://shields.io)](https://opensource.org)

This repository contains the raw experimental datasets, data analysis scripts, and supplementary tables for the evaluation of a three-channel gas-diffusion flow cell electrolyser designed for Martian CO₂ conversion.

The system explores the simultaneous electrochemical reduction of CO₂ into CO and O₂ under room-temperature conditions using sulphate electrolytes (Na₂SO₄ and K₂SO₄) as a proposed In Situ Resource Utilisation (ISRU) process for future Mars missions.

---

## 🚀 Overview & System Architecture

Unlike standard H-cells or zero-gap MEA configurations, this system features a **three-channel flow cell architecture** equipped with a Cation Exchange Membrane (CEM):
1. **Cathode Gas Channel:** Continuous feed of simulated Martian CO₂ gas.
2. **Liquid Catholyte Channel:** Flowing sulphate electrolyte to maintain local pH stability.
3. **Liquid Anolyte Channel:** Flowing electrolyte for the oxygen evolution reaction (O₂).


## 📊 Data Processing & Hardware Corrections

A core contribution of this dataset is the high-fidelity tracking of electrical hardware constraints. Faradaic efficiencies (FE) and energy efficiencies (EE) are strictly calculated using **actually delivered currents** rather than nominal software set-points.

### Key Considerations:
* **Hardware Current Offsets:** At low current regimes (0.1 A nominal), a standard power supply introduced a +16% baseline offset (delivering up to 0.116 A), while high-precision units maintained stability (0.0998 A). The text and scripts correct for this variation automatically.
* **Low-Current Data Filtering:** Data points at the lowest current step (0.1 A) that yielded unphysical FE > 100% (even after flow rate and current corrections) were filtered out. This artifact is attributed to low product flow rates causing gas accumulation inside the three-channel plumbing lines.

All uncorrected raw values and full comparative distributions across the 18 experimental runs are cataloged in **Table S5** within the repository.

---

## 📁 Repository Structure

```text
├── data/
│   ├── raw/                 # Unprocessed chromatographic peak areas and GC logs
│   └── processed/           # Curated data used for figures (filtered low-current artifacts)
├── scripts/
│   ├── data_analysis.py     # Python script calculating Faradaic and Energy efficiencies
│   └── plot_generation.py   # Code for creating the publication-ready figures
├── supplementary/
│   └── Table_S5_offsets.csv # Delivered currents, nominal set-points, and mA deviations
├── LICENSE
└── README.md
```

---

## 🛠️ Getting Started

### Prerequisites
To run the analysis scripts and recreate the figures, you will need Python 3.x and the following libraries:
```bash
pip install numpy pandas matplotlib seaborn
```

### Running the Analysis
1. Clone this repository:
   ```bash
   git clone https://github.com
   cd martian-co2-electrolyser
   ```
2. Execute the primary analysis script to process the raw data from `data/raw/` and apply the hardware calibration curves:
   ```bash
   python scripts/data_analysis.py
   ```

---

## 🔗 Data Citation

The complete, immutable raw dataset and analytical logs are permanent-archived on Zenodo:
> **Citation:** *[Paulina Govea-Alvarezab, Jia Songb, Zhiyuan Chen, Deepak Pant, Kevin M. Van Geem, Yi Ouyang]. (2026). Electrochemical CO2 reduction to CO towards Mars ISRU. Zenodo.  DOI 10.5281/zenodo.21945042*

