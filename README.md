# Diabetes Patient Readmission Analysis

## Project Overview

This project analyzes a large healthcare dataset of diabetes patients to investigate demographic, clinical, and treatment factors associated with hospital readmission. The objective is to identify patterns that may help support earlier detection of complications and improve patient management.

The project includes data cleaning, exploratory data analysis (EDA), KPI evaluation, visualization, and machine learning model comparison. Python was used for data preparation and analysis, while Tableau was used to visualize key insights.

The initial goal of the analysis was to explore factors contributing to diabetes detection and hospital readmission outcomes using real-world patient records. 

---

# Dataset

The dataset used in this project contains detailed information about patients with diabetes, including demographic characteristics, medical interventions, laboratory results, and hospital readmission outcomes.

### Dataset characteristics

**Original dataset**

* 101,766 patient records
* 50 attributes

**Cleaned dataset used for analysis**

* 55,394 records
* 44 variables

The dataset contains both numerical and categorical variables, allowing multiple analytical approaches.

### Data categories

**Demographic variables**

* race
* gender
* age
* weight

**Clinical activity**

* time_in_hospital
* num_lab_procedures
* num_procedures
* num_medications
* number_outpatient
* number_inpatient
* number_diagnoses

**Diagnosis information**

* diag_1
* diag_2
* diag_3

**Medication variables**
Examples include:

* metformin
* insulin
* glyburide
* glipizide

**Laboratory test indicators**

* max_glu_serum
* a1cresult

**Outcome variable**

* `readmitted`

Readmission categories:

* `<30` — patient readmitted within 30 days
* `>30` — patient readmitted after 30 days
* `NO` — no readmission recorded

The dataset also contains additional metadata such as admission type identifiers and treatment indicators. 

---

# Project Workflow

The project follows a structured data analysis pipeline:

```text
Raw Dataset → Data Cleaning → Exploratory Analysis → Visualization → Model Evaluation
```

Three main notebooks implement the workflow.

---

# Notebook 1 — Data Cleaning

**File:** `data_cleaning.ipynb`

### Objective

Prepare the raw dataset for analysis by resolving inconsistencies, handling missing values, and transforming features.

### Tools

* Python
* pandas
* NumPy
* matplotlib

### Key steps

**Initial inspection**

* checked dataset structure and data types
* identified missing values
* removed duplicate records

**Handling missing data**
Several strategies were applied depending on the feature type:

* median imputation for numeric variables
* categorical replacement (e.g., “Unknown”) for missing categorical data

Example:
The `weight` column contained a large number of missing values and was imputed using the median.

**Feature engineering**
Example transformation:

`number_emergency` → `emergency_history` (binary indicator)

**Feature reduction**
Low-value or redundant variables were removed to simplify the dataset and reduce dimensionality.

The resulting cleaned dataset was saved for exploratory analysis.

---

# Notebook 2 — Exploratory Data Analysis

**File:** `exploratory_analysis.ipynb`

### Objective

Explore patterns and relationships between patient characteristics and readmission outcomes.

### Tools

* pandas
* matplotlib
* seaborn

### Analysis techniques

**Distribution analysis**
Examined distributions of key variables including:

* age
* medication count
* race
* gender
* laboratory test results

Visualization techniques included:

* histograms
* count plots
* pie charts

---

### Relationship analysis

Relationships between variables were explored using:

* correlation heatmaps
* scatterplots
* grouped comparisons

Examples examined:

* age vs number of medications
* age vs hospital stay length
* race vs readmission
* gender vs readmission
* insulin treatment vs readmission

---

### Multivariate analysis

Pairplots were used to explore interactions among multiple variables:

* age
* num_medications
* time_in_hospital
* number_diagnoses

Readmission category was used as the grouping variable.

FacetGrid visualizations were also used to explore subgroup patterns across gender and race.

---

### KPI Analysis

Several key performance indicators were calculated:

* average age by readmission category
* average medication count
* average hospital stay duration
* readmission distribution
* laboratory test distributions

These metrics helped highlight variables potentially associated with higher readmission risk.

---

# Notebook 3 — Model Evaluation

**File:** `model_evaluation.ipynb`

### Objective

Evaluate machine learning models for predicting hospital readmission.

### Tools

* scikit-learn
* pandas
* NumPy

### Models tested

Five classification algorithms were implemented:

* Decision Tree
* Random Forest
* Logistic Regression
* K-Nearest Neighbors (KNN)
* Support Vector Machine (SVM)

Hyperparameter tuning was performed using:

* Randomized Search
* Grid Search

Model performance was evaluated using:

* confusion matrices
* classification reports
* accuracy metrics

ROC curves were attempted but ultimately excluded due to issues caused by severe class imbalance in the dataset. 

---

### Model Results

| Model               | Accuracy |
| ------------------- | -------- |
| Decision Tree       | ~56%     |
| Random Forest       | ~60%     |
| Logistic Regression | ~60%     |
| KNN                 | ~58%     |

Random Forest and Logistic Regression produced the most stable performance across the dataset. 

However, all models struggled with predicting minority classes due to dataset imbalance.

---

# Tableau Visualization

Three Tableau visualizations summarize key insights from the analysis.

## Age Distribution by Readmission Status

This visualization compares readmission outcomes across age groups.

Observations:

* Most patients fall within the 65–75 age range.
* Older groups show slightly higher readmission counts.
* The majority of patients across all age groups were not readmitted.

---

## Readmission Proportion

This chart shows the distribution of readmission outcomes.

Observations:

* Most patients were not readmitted.
* A smaller proportion were readmitted after 30 days.
* The smallest group were readmitted within 30 days.

This imbalance explains why predictive models struggled to correctly classify the minority readmission categories.

---

## Average Hospital Stay by Readmission Category

This visualization compares average hospital stay duration across readmission groups.

Observations:

* Patients readmitted within 30 days had the longest average hospital stay.
* Patients with no readmission had shorter stays.

This suggests that longer hospital stays may be associated with more severe cases and increased readmission risk.

---

# Key Insights

* Older patients show slightly higher readmission frequencies.
* Patients with longer hospital stays tend to have higher readmission risk.
* Medication counts and diagnosis counts correlate with hospitalization patterns.
* The dataset contains strong class imbalance, affecting predictive model performance.
* Random Forest and Logistic Regression produced the most stable results.

---

# Technologies Used

**Programming**

* Python

**Data Analysis**

* pandas
* NumPy

**Visualization**

* matplotlib
* seaborn
* Tableau

**Machine Learning**

* scikit-learn

---

# Note

A smaller sample dataset is included for demonstration purposes. The full dataset used for analysis is significantly larger.

