# Exploratory Data Analysis on the TARGET ALL Phase II Dataset

## 📘 Introduction

This repository contains an in-depth exploratory data analysis (EDA) of the **TARGET ALL Phase II** dataset, a valuable and complex clinical dataset focusing on pediatric patients affected by **acute lymphoblastic leukemia (ALL)**, particularly those who experienced **early bone marrow relapse**. The dataset originates from the [cBioPortal](https://www.cbioportal.org/study/clinicalData?id=all_phase2_target_2018_pub) and represents a cornerstone of translational research aimed at improving risk stratification, treatment strategies, and clinical outcomes in pediatric leukemia.

The analysis aims to provide both a **statistical exploration** and **clinical interpretation** of the dataset, serving as a foundational step toward future predictive modeling and decision support tools in pediatric oncology.

---

## 🎯 Project Goals

The primary objectives of this exploratory analysis are to:

- Understand the **structure and limitations** of the dataset.
- Identify **highly informative features** and possible data quality issues (e.g., missingness, duplication).
- Evaluate **correlations** between clinical, demographic, and genomic variables.
- Investigate **biologically and clinically relevant patterns**, such as relapse behavior, MRD dynamics, and survival indicators.
- Lay the groundwork for **predictive modeling** (e.g., survival, relapse risk, MRD classification).

---

## 🧬 Dataset Description

The dataset includes:

- **1,978 rows** corresponding to clinical samples.
- **55 features** capturing demographic, clinical, genomic, and molecular details.
- **1,551 unique patients**.

### Key Variables:

- **Demographic:** `Diagnosis Age`, `Sex`, `Ethnicity`, `Race`
- **Clinical status and outcomes:** `Overall Survival`, `Time To Event`, `First Event`, `Survival Status`
- **Disease characteristics:** `Bone Marrow Blasts` (Day 8, 15, 29), `MRD Percentages`, `CNS/Bone Marrow/Testes Relapse`
- **Genetic alterations:** `BCR-ABL1`, `MLL`, `ETV6-RUNX1`, `TCF3-PBX1`, `DNA Index`
- **Blood-related variables:** `WBC`, `Mutation Count`, `TMB (nonsynonymous)`
- **Treatment-related information:** `Protocol`, `Alternative Therapy`

---

## 🧹 Data Preprocessing and Cleaning

Key steps included:

- **Null value inspection:** Many features show high levels of missingness (e.g., `MRD Day 43` with 100%, `Other Alternative Therapy Given` with >99%). These were flagged for removal or cautious interpretation.
- **Duplicate rows:** Identified and removed based on relevant clinical variables, excluding unique identifiers and high-missing features.
- **Variable filtering:** Features with low utility or overwhelming missing data were excluded to streamline the analysis.
- **Collinearity check:** Strong correlations were identified (e.g., `Diagnosis Age` vs. `Diagnosis Age (days)` ~0.9986), and recommendations were made to retain only one per pair.

---

## 📊 Visualizations and Analytical Results

The EDA includes comprehensive plots and statistics to assess the distribution and relationships of the most relevant variables.

### Examples:

- **Numerical distributions** (e.g., WBC, DNA Index, Survival Days)
- **Boxplots and histograms** (e.g., MRD across treatment timepoints)
- **Correlation matrix:** to detect strong linear dependencies
- **Chi-square test results:** showing statistically significant associations (e.g., between CNS relapse and bone marrow relapse with p < 2×10⁻⁸)
- **Scatter plots with regression lines:** e.g., `Blasts Day 29` vs `MRD Day 29`

---

## 🧠 Clinical Interpretation

Beyond raw statistical insights, the report contextualizes findings from a clinical standpoint:

- **MRD (Minimal Residual Disease):** A strong indicator of prognosis, often measured at Days 8, 15, 29, and post-consolidation.
- **Blast percentages:** Key to disease classification and early treatment response assessment.
- **Survival metrics:** Used to stratify patients and evaluate the impact of treatment protocols.
- **Associations between relapse locations:** CNS involvement correlates strongly with simultaneous bone marrow relapse.

---

## 🔍 Toward Predictive Modeling

This EDA is designed as a **pre-modeling phase** to guide the development of machine learning models in the future.

### Candidate targets:

- `Overall Survival Status` (binary classification)
- `Time To Event` (survival regression)
- `First Event` (multiclass classification)
- `MRD Day 29 > 0.01%` (high-risk identification)

### Candidate features:

- Age, WBC, Sex, DNA Index
- Genetic fusion statuses (BCR-ABL1, etc.)
- MRD and Blasts (Day 15, Day 29)
- CNS and Trisomy status

### Modeling strategies (suggested):

| Objective                       | Suggested Models                       |
|--------------------------------|----------------------------------------|
| Binary survival classification | Logistic Regression, XGBoost, Random Forest |
| Time-to-event prediction       | Cox Proportional Hazards               |
| MRD classification             | Logistic Regression with thresholding  |
| Risk stratification            | Clustering + Decision Trees            |

---

## ⚙️ Technical Stack

This analysis was performed using Python and the following libraries:

- `pandas`, `numpy` for data manipulation
- `matplotlib`, `seaborn` for visualization
- `scikit-learn` for preprocessing and modeling
- `lifelines` for survival analysis
- `scipy`, `statsmodels` for statistical testing

---

## 📄 Future Work

Planned developments include:

- Survival prediction models using Kaplan-Meier curves and Cox regression
- Risk scoring systems to guide treatment intensification
- Data imputation strategies for sparse but important clinical variables
- Documentation of model interpretability and deployment considerations

---

## 🔗 Additional Documentation

A full write-up of the **clinical-documentary analysis** and **modeling results** is available here:

👉 [**Link to final report**](https://docs.google.com/document/d/1_3aopjR9agKB9zPe5QdAgzEv-5e0OzoKkTZZTaMmtF8)

---

## 📜 License & Acknowledgments

- Data: TARGET ALL Phase II study, available via [cBioPortal](https://www.cbioportal.org/)
- Author: Francesco Cardinale
- This project is intended for research and educational purposes only.
