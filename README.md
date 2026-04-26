# COVID-19 Variant tracking in California between 2021 through 2023
### BIFX-546: Machine Learning for Bioinformatics — Spring 2026

**Author:**
- Amanda Graham (asg6@hood.edu)

**Instructor:**
- Dr. Sarangan Ravichandran
---

## 🎯 Project Goal

Can we predict the next circulating variant of COVID-19 based on a selection of features?

We hypothesize that there is typically one predominant circlulating variant of COVID-19 during a timeframe. Using a set of features such as the number of specimens collected, the percentage of specimens collected and the change in variant specimens collected per day we can predict the next predominant circulating variant.

---

## 📊 Dataset

| Field | Details |
|---|---|
| **Name** | COVID-19 Variant Data |
| **Source** | Kaggle Repository |
| **URL** | [https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008](https://www.kaggle.com/datasets/nidzsharma/covid-19-variant-data) |
| **Size** | 5802 specimens collected, 8 features, 7790 rows of data |
| **Data Collector** | California Department of Public Health (CDPH) |

The dataset contains COVID-19 variant data collected including date, area (California), area type (state), variant name, number of specimens collected, percentage of specimens collected, specimens 7 day average and the percentage 7 day average.

---

## 🧠 Techniques Used NEED TO UPDATE THIS!!!

| Phase | Technique | Course Week | 
|---|---|---|
| EDA | Descriptive statistics (mean, median, std, IQR) | Week 5 |
| EDA | Distribution plots, correlation heatmap, bar charts | Week 3 |
| Analysis | Chi-square test of independence (readmission vs. diagnosis group) | Week 6 |
| Analysis | Bootstrap confidence intervals on readmission rate | Week 6 |
| Modeling | Logistic Regression with train/test split (80/20) | Week 10 |
| Modeling | Decision Tree for feature importance comparison | Week 11 |
| Evaluation | Accuracy, Precision, Recall, AUC-ROC | Week 10–11 |

---

## 📁 Repository Structure NEED TO UPDATE THIS!!!

```
diabetes-readmission/
├── notebooks/
│   ├── 01_eda.ipynb              # Data loading, cleaning, EDA
│   ├── 02_hypothesis_testing.ipynb  # Statistical tests
│   └── 03_modeling.ipynb         # Logistic regression + decision tree
├── data/
│   └── README_data.md            # Link to UCI source; raw file not included (>50MB)
├── results/
│   ├── fig1_readmission_by_age.png
│   ├── fig2_correlation_heatmap.png
│   ├── fig3_roc_curve.png
│   └── table1_model_metrics.csv
├── src/
│   └── preprocess.py             # Reusable cleaning functions
├── README.md
└── requirements.txt
```

---

## ⚙️ How to Run NEED TO UPDATE THIS !!!

### Option 1 — Google Colab (recommended, no install needed)

1. Open [Google Colab](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste this repo URL and select the notebook you want to run
4. Run the first cell to install dependencies:
   ```python
   !pip install -r requirements.txt
   ```
5. Run all cells: **Runtime → Run all**

> **Note:** The dataset is downloaded automatically in the first notebook cell from the
> Kaggle URL. No manual download required.

### Option 2 — Local Jupyter NEED TO UPDATE THIS !!!

```bash
# Clone the repo
git clone https://github.com/aspurser84-dot/BIFX546-project.git

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

Open notebooks in order: `01_eda.ipynb` → `02_hypothesis_testing.ipynb` → `03_modeling.ipynb`

---

## 📈 Key Results & Plots

| Figure | File | Description |
|---|---|---|
| Fig 1 | `results/Fig1_Distribution_of_Variants.png` | Number of specimens collected per variant (box plot) |
| Fig 2 | `results/Fig2_Specimens_Collected_Over_Time.png` | Number of specimens collected over time by variant (scatter plot) |
| Fig 3 | `results/Fig3_Percentage_Variants_Over_Time.png` | Percentage of specimens collected over time by variant (scatter plot) |
| Fig 3 | `results/Fig4_Rate_of_change_per_Variant.png` | Rate of change per variant over time (line plot) |
| Fig 3 | `results/Fig5_7day_avg_rate_of_change_per_variant.png` | 7 day average rate of change per variant over time (line plot) |

**Model performance summary:**

| Model | Accuracy | Precision | Recall |
|---|---|---|---|---|
| Random Forest | 0.65 | 1.0 | 0.65 |

---

## Early Insights:
This dataset provides insight on the predominant variant over time. 
Some instances of multiple variants circulating, for the most part one variant becomes the predominant variant for a short period of time. 
As that variant starts to decrease, we can see another variant increase and become the predominant variant

## 📝 Summary of Findings NEED TO UPDATE THIS !!!
The logistic regression model achieved an AUC-ROC of 0.79, outperforming the
decision tree (0.74). The three strongest predictors of readmission were number of
inpatient visits in the prior year, number of diagnoses recorded at discharge, and
HbA1c result. These findings suggest that care-transition planning — particularly for
high-comorbidity patients with prior hospitalizations — may be the highest-yield
intervention target. Limitations include the dataset's age (1999–2008) and the
exclusion of social determinants of health, which likely confound readmission risk.

---

## 📦 Dependencies NEED TO UPDATE THIS !!!

See `requirements.txt`. Core packages:

```
pandas>=1.5
numpy>=1.23
matplotlib>=3.6
seaborn>=0.12
scikit-learn>=1.2
scipy>=1.10
jupyter
```

---

## 📜 References NEED TO UPDATE THIS !!!

1. Strack, B., DeShazo, J.P., et al. (2014). Impact of HbA1c Measurement on Hospital
   Readmission Rates: Analysis of 70,000 Clinical Database Patient Records.
   *BioMed Research International*, Article ID 781670.
   https://doi.org/10.1155/2014/781670

2. UCI Machine Learning Repository. (2014). Diabetes 130-US Hospitals Dataset.
   https://archive.ics.uci.edu/dataset/296

3. Grus, J. (2019). *Data Science from Scratch* (2nd ed.). O'Reilly Media.

---

*BIFX-546 · Hood College · Spring 2026 · Dr. Sarangan Ravichandran*

