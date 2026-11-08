# Heart Disease Risk Factors: A Statistical Analysis with Logistic Regression

## Overview

This project investigates which clinical features are statistically significant predictors of coronary artery disease using the Cleveland Heart Disease dataset from the UCI Machine Learning Repository.

Rather than treating this as a pure machine learning task, the focus is on **statistical rigour**: checking model assumptions, interpreting coefficients as odds ratios, and being honest about the limits of what this dataset can tell us.

---

## Research Question

> Which patient characteristics are the strongest predictors of heart disease presence, and how large is their effect?

---

## Dataset

| Property      | Detail                                                                         |
| ------------- | ------------------------------------------------------------------------------ |
| Source        | UCI Machine Learning Repository                                                |
| Link          | [Heart Disease Dataset](https://archive.ics.uci.edu/ml/datasets/Heart+Disease) |
| Patients      | 297 (after removing 6 rows with missing values)                                |
| Features      | 13 clinical variables                                                          |
| Target        | Binary: disease present (1) or absent (0)                                      |
| Class balance | 54% negative, 46% positive                                                     |

### Features used

- `age` — patient age in years
- `sex` — 1 = male, 0 = female
- `cp` — chest pain type (0–3)
- `trestbps` — resting blood pressure (mm Hg)
- `chol` — serum cholesterol (mg/dl)
- `fbs` — fasting blood sugar > 120 mg/dl
- `restecg` — resting ECG results
- `thalach` — maximum heart rate achieved
- `exang` — exercise-induced angina
- `oldpeak` — ST depression induced by exercise
- `slope` — slope of peak exercise ST segment
- `ca` — number of major vessels coloured by fluoroscopy
- `thal` — thalassemia type

---

## Methods

1. **Data cleaning** — handled missing values (marked as `?` in source), binarised the target variable
2. **Exploratory analysis** — disease rates by sex and exercise angina, distribution plots
3. **Assumption checks** — multicollinearity via correlation matrix, events-per-predictor ratio
4. **Modelling** — logistic regression with standardised continuous features, stratified 80/20 train-test split
5. **Interpretation** — coefficients converted to odds ratios with plain-language explanation

---

## Results

| Metric                    | Score |
| ------------------------- | ----- |
| Accuracy                  | 86.4% |
| Precision (disease class) | 87.1% |
| Recall (disease class)    | 85.2% |
| F1-score (disease class)  | 86.1% |
| ROC-AUC                   | 0.923 |

### Top predictors (by odds ratio)

| Feature                  | Odds Ratio | Interpretation                                    |
| ------------------------ | ---------- | ------------------------------------------------- |
| Thalassemia type (thal)  | 2.41       | Reversible defect strongly increases risk         |
| Vessels coloured (ca)    | 2.18       | Each vessel nearly doubles the odds               |
| Chest pain type (cp)     | 1.95       | Atypical presentation associated with higher risk |
| Exercise angina (exang)  | 1.74       | Pain during exercise is a warning sign            |
| Max heart rate (thalach) | 0.68       | Higher fitness is protective                      |

---

## Key Finding

Thalassemia type, number of fluoroscopy-coloured vessels, and chest pain type are the three strongest predictors of heart disease in this dataset. Higher maximum heart rate is the strongest protective factor. Cholesterol showed a surprisingly weak signal — a known limitation of this small clinical sample, not a general finding.

---

## Limitations

- 297 patients from a single hospital in Cleveland, Ohio — not population-representative
- Data collected in the 1980s; clinical practice has changed
- The weak cholesterol signal should not be interpreted as evidence that cholesterol is unimportant
- Model is for statistical learning purposes only — not a clinical diagnostic tool

---

## Repository Structure

```
heart-disease-risk-analysis/
├── heart_disease_analysis.ipynb   # Full notebook with code, outputs, and commentary
├── heart_disease_analysis.py      # Clean Python script version
└── README.md
```

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/yourusername/heart-disease-risk-analysis
cd heart-disease-risk-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels

# Run the script
python heart_disease_analysis.py
```

The dataset is loaded directly from the UCI repository URL — no manual download needed.

---

## Also on Kaggle

The full notebook with visualisations and markdown commentary is published on Kaggle: [View notebook →](https://www.kaggle.com/raihanrahamatullah)

---

## References

- Detrano, R. et al. (1989). International application of a new probability algorithm for the diagnosis of coronary artery disease. *American Journal of Cardiology, 64*(5), 304–310.
- UCI Machine Learning Repository. Heart Disease Dataset. https://archive.ics.uci.edu/ml/datasets/Heart+Disease

---

## Author

Raihan Rahamatullah — Statistics student, JKKNIU [Kaggle](https://www.kaggle.com/raihanrahamatullah) · [GitHub](https://github.com/ador-23)


