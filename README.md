# One Dataset, Different Questions: What ML Can (and Cannot) Tell MOF Chemists About CO₂ Adsorption

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## Abstract

I reproduced a machine learning study that predicted CO₂ adsorption in metal-organic frameworks. The original paper reported R² = 0.90 and concluded that pressure and temperature are the most important variables. As a chemist, I wanted to know something different: if my capture system operates at a fixed pressure, which MOF should I choose? By splitting the dataset into low-pressure and high-pressure regimes, I found that metal identity matters four times more at low pressure than at high pressure. The models don't predict uptake accurately (R² ≈ 0.25), but they reveal something useful: the design rules for MOF CO₂ capture depend on your operating conditions. One model for all pressures gives one answer. Different questions give different answers.

## The Paper

Li, X., et al. (2023). *Applied machine learning to analyze and predict CO₂ adsorption behavior of metal-organic frameworks.* Carbon Capture Science & Technology, 9, 100146.

**Their finding:** Pressure and temperature are the most important variables for CO₂ uptake. R² = 0.90.

**My question as a chemist:** I can't change the pressure in my capture system. Which MOF should I choose?

## What I Did

1. Reproduced their Random Forest model — their numbers are correct
2. Removed pressure and temperature — R² dropped to 0.28
3. Split the data by pressure regime — different applications need different answers
4. Trained separate models for low pressure and high pressure
5. Compared what features matter in each regime

## What I Found

| Feature | Low Pressure | High Pressure |
|:---|:---|:---|
| Application | Flue gas capture | Storage |
| Metal importance | 25% | 6% |
| Texture importance | 75% | 94% |
| Design rule | Optimize metal AND porosity | Maximize surface area |

At low pressure, metal identity matters 4× more than at high pressure.

If you're designing a MOF for flue gas capture, Cu and Ni are strong candidates. If you're designing for storage, maximize BET surface area.

## Honest Limitations

- Low-pressure model R² = 0.25 (poor prediction)
- High-pressure model R² = negative (too few samples)
- The dataset is too small for reliable regime-specific models

These models do not predict uptake accurately. They reveal relative importance of features.

## The Lesson

The question you ask determines the answer you get.

Li et al. asked: "What predicts uptake across all conditions?" Answer: pressure.

I asked: "At MY operating pressure, what matters?" Answer: it depends on the pressure.

Neither question is wrong. They serve different purposes.

## Repository Structure

- analysis.ipynb — Complete notebook
- Table_S3.csv — Dataset from Li et al. (2023)
- figures/ — Generated plots

## Quick Start

git clone https://github.com/vahidsafarifard/MOF-CO2-Regime-Analysis.git
cd MOF-CO2-Regime-Analysis
jupyter notebook analysis.ipynb

## Dependencies

Python 3.8+, pandas, numpy, scikit-learn, matplotlib, seaborn

## Reference

Li, X., et al. (2023). Applied machine learning to analyze and predict CO₂ adsorption behavior of metal-organic frameworks. *Carbon Capture Science & Technology*, 9, 100146.

## Author

Vahid Safarifard

## License

MIT
