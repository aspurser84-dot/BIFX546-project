# COVID-19 Variant tracking in California between 2021 through 2023
### BIFX-546: Machine Learning for Bioinformatics — Spring 2026

**Author:**
- Amanda Graham (asg6@hood.edu)

**Instructor:**
- Dr. Sarangan Ravichandran
---

## 🎯 Project Goal

Can we predict the next circulating variant of COVID-19 based on a selection of features?

We hypothesize that there is typically one predominant variant of COVID-19 circlulating during a time frame. Using a set of features such as the number of specimens collected, the percentage of specimens collected and the rate change in variant specimens collected per day and 7 day averages for these features, we can predict the next predominant circulating variant using a Random Forest model.

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

## 🧠 Techniques Used

| Phase | Technique |
|---|---|
| EDA | Descriptive statistics (count, average, standard deviation, minimum, quantiles, and the maximum) |
| Data Cleaning | Convert data types, remove variables, calculate 7 day averages, calculate rate change, remove zero values |
| EDA | Distribution of Variants, Number of Specimens Collected Over Time by Variant, Percentage of Variants Over Time, Rate of Change per Variant and 7 Day Rate of Change per Variant |
| Modeling | Establishing threshold on feature 'percentage' |
| Modeling | Stratify train/test split (80/20) |
| Modeling | Random Forest model, Training Accuracy, OOB Score, Class Distribution and Weights |
| Evaluation | Testing Accuracy, Precision, Recall, f1 score, Confusion Matrix |

# Modeling Approach and Justification

#### A Random Forest model was chosen based on the dataset containing labeled data and the goal of predicting a acategory (variant).
---

## 📁 Repository Structure

```
BIFX546-project/
├── data/
│   └── covid19_variant.csv                             # raw CSV file included (409KB)
├── notebooks/
│   ├── Final_project_BIFX546_Graham.ipynb              # Data loading, cleaning, EDA, Random Forest Modeling and Evaluation
│   ├── Supplemental.ipynb  # Statistical tests         # Additional modeling attempted
                                                         including Time series split using RF, Balanced RF,
                                                          Easy Ensemble model and SMOTE
├── results/
│   ├── Fig1_Distribution_of_Variants.png
│   ├── Fig2_Specimens_Collected_Over_Time.png
│   ├── Fig3_Percentage_Variants_Over_Time.png
│   ├── Fig4_Rate_of_Change_per_Variant.png
│   ├── Fig5_Average_Rate_of_Change_per_Variant.png
│   └── Fig6_Confusion_Matrix
├── src/
│   └── .gitkeep                                       # Optional folder for temp
├── README.md
└── requirements.txt
```

---

## ⚙️ How to Run

### Option 1 — Google Colab (recommended, no install needed)

1. Open [Google Colab](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste this repo URL and select the notebook you want to run.
4. Run the first cell to install dependencies:
   ```python
   !pip install -r https://raw.githubusercontent.com/aspurser84-dot/BIFX546-project/main/requirements.txt
   ```

5. Run the second cell set up the directory.

6. Run one of the two upload options:

    Option 1. Download the covid19_variant.csv file from this repository data folder -> run the third cell -> choose the covid19_variant.csv file from the downloads folder.

    Option 2. Recommended. Run the fourth cell.

8. Run all cells: **Runtime → Run focused cell and all cells below**

> **Note:** The dataset is downloaded automatically in the second download option from the
> Kaggle URL. No manual download required.

---

## 📈 Key Results & Plots

| Figure | File | Description |
|---|---|---|
| Fig 1 | `results/Fig1_Distribution_of_Variants.png` | Number of specimens collected per variant (box plot) |
| Fig 2 | `results/Fig2_Specimens_Collected_Over_Time.png` | Number of specimens collected over time by variant (scatter plot) |
| Fig 3 | `results/Fig3_Percentage_Variants_Over_Time.png` | Percentage of specimens collected over time by variant (scatter plot) |
| Fig 4 | `results/Fig4_Rate_of_Change_per_Variant.png` | Rate of change per variant over time (line plot) |
| Fig 5 | `results/Fig5_Average_Rate_of_Change_per_Variant.png` | 7 day average rate of change per variant over time (line plot) |
| Fig 6 | `results/Fig6_Confusion_Matrix.png` | Confusion Matrix of final Random Forest model |

**Model performance summary:**

| Model | Accuracy | Precision | Recall | f1 Score |
|---|---|---|---|---|
| Random Forest | 76.45% | 77.80% | 76.45% | 76.84% |
 
---

## Early Insights:
This dataset provides insight on the predominant variant over time. There are some instances of multiple variants circulating in the dataset. However, for the most part one variant becomes the predominant variant for a short period of time. As that variant starts to decrease, we can see another variant increase and become the predominant variant. Using a set of features such as the number of specimens collected, percentage of specimens collected, specimens 7 day average, the percentage 7 day average, rate of change and the 7 day average rate of change a Random Forest model was trained and tested. Further refinement to the model was made to implement a threshold cutoff for the variable 'percentage'.

## 📝 Summary of Findings
Using a Random Forest model with a threshold cutoff on the variable 'percentage' proves to be the best Random Forest model. The original model training accuracy reached 100% but the OOB score was low at 76.6% with a testing accuracy at 76%. Adding additional trees did not have much of an impact on the OOB score. The most important factor for the model was stratifying the splitting so that there was a larger distribution of all variants present in the training and testing dataset. Splitting the dataset using time series split proved to limit the testing dataset to only four variants present (see supplemental notebook). This threshold cutoff allowed all eight variants to be trained and tested on. However it is possible to increase this threshold cutoff to 30% which increases the testing accuracy, precision, recall and f1 score up to 90% however, this comes at a cost of removing variants present in low abundace and only four variants would be found in the testing and training dataset.

---

## 📦 Dependencies

See `requirements.txt`. Core packages:

```
pandas>=1.5
numpy>=1.23
matplotlib>=3.6
seaborn>=0.12
scikit-learn>=1.2
```

---

## 📜 References

1. Kagglehub Repository. COVID-19 Variant Data.
   https://www.kaggle.com/datasets/nidzsharma/covid-19-variant-data

2. Grus, J. (2019). *Data Science from Scratch* (2nd ed.). O'Reilly Media.

---

*BIFX-546 · Hood College · Spring 2026 · Instructor: Dr. Sarangan Ravichandran*
