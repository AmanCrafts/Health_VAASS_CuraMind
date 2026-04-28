# Health VAASS CuraMind — Project Report

**Sector:** Healthcare Analytics
**Institute:** Newton School of Technology
**GitHub Repository:** https://github.com/AmanCrafts/Health_VAASS_CuraMind
**Date:** 28 April 2026

**Team Members:**
| Name | Role |
|---|---|
| Shubhi Kumari | Cleaning, Preprocessing, EDA, Statistical Analysis |
| Amanjeet Malik | Cleaning, Preprocessing, EDA, Statistical Analysis |
| Vansh Dagar | Tableau Dashboard |
| Anishka Khurana | Tableau Dashboard |
| Shorya Taneja | Report Writing |

---

## Executive Summary

The healthcare industry generates large volumes of patient data, yet extracting actionable insights from this data remains a significant challenge. This project, **Health VAASS CuraMind**, focuses on analysing patient health records to uncover patterns that can improve patient outcomes, optimise treatment strategies, and support data-driven healthcare decisions.

The dataset was sourced from Kaggle and consists of raw patient health records containing demographic details, medical conditions, treatments, and outcomes. The dataset required extensive preprocessing due to missing values, inconsistent formats, and categorical variations. A complete ETL pipeline was implemented in Python using Jupyter Notebooks, ensuring data cleaning, transformation, and reproducibility.

Exploratory Data Analysis (EDA) was conducted to identify trends, distributions, and relationships across variables. Statistical techniques such as correlation analysis and regression were applied to uncover deeper insights into the factors influencing patient health outcomes.

An interactive Tableau dashboard was developed to allow stakeholders to explore key metrics dynamically. The dashboard provides a decision-support system by highlighting patterns across demographics, treatment effectiveness, and condition distribution.

Key insights revealed that certain demographic groups are more prone to specific conditions, while treatment effectiveness varies significantly across patient segments. Based on these findings, actionable recommendations were proposed to improve healthcare resource allocation, preventive care strategies, and treatment planning.

This project demonstrates the ability to perform end-to-end data analytics, combining technical implementation with business-focused insights to support better decision-making in the healthcare sector.

---

## Problem Statement & Objectives

### Problem Statement

The primary problem addressed in this project is the lack of actionable insights from raw healthcare data, which limits the ability of healthcare providers to make informed decisions regarding patient care and resource allocation.

### Objectives

- Analyse patient health data and identify key factors affecting patient outcomes
- Uncover patterns across demographic groups and medical conditions
- Evaluate treatment effectiveness across different patient segments
- Build a data-driven dashboard for decision support

### Scope

The project focuses on analysing structured patient health records and deriving insights using statistical and visualisation techniques. Advanced predictive modelling is considered out of scope.

### Success Criteria

- Clean and analysis-ready dataset
- Meaningful insights derived from EDA and statistical analysis
- Functional Tableau dashboard with decision-making capabilities
- Actionable business recommendations

---

## Dataset Description

The dataset was sourced from Kaggle:
**https://www.kaggle.com/datasets/mursaleen880/patient-health-record-raw-csv**

It consists of **1,715+ records** across **17 columns** capturing patient demographics, medical conditions, and treatment-related information.

### Key Columns

| Column | Description |
|---|---|
| `Patient_ID` | Unique patient identifier |
| `Name` | Patient name (anonymised in processing) |
| `Age` | Patient age |
| `Gender` | Patient gender |
| `City` | Patient city of residence |
| `BMI` | Body Mass Index |
| `Blood_Pressure` | Blood pressure reading (systolic/diastolic) |
| `Heart_Rate` | Heart rate (bpm) |
| `Cholesterol_Level` | Cholesterol level |
| `Diabetic` | Diabetic status (yes/no) |
| `Smoker` | Smoking status |
| `Medications` | Current medications |
| `Last_Visit_Date` | Date of last hospital visit |
| `Follow_Up` | Follow-up interval (days) |
| `Diagnosis_Code` | ICD diagnosis code (A00, B20, E11.9, I10, etc.) |
| `Notes` | Clinical notes |
| `Has_Disease` | Disease presence indicator (0/1) |

### Data Quality Issues Identified in Raw Data

- Age values entered as text (e.g., `"twenty"`) or invalid numbers (e.g., `-5`, `250`)
- BMI values with units appended (e.g., `"22kg/m2"`)
- Blood pressure in multiple formats (`"120 over 80"`, `"120 - 80"`, `"120/80"`)
- Heart rate entered as text (e.g., `"eighty"`) or physiologically impossible values (`0`, `500`)
- Inconsistent gender labels (`"FEMALE"`, `"F"`, `"female"`, `"male"`, `"M"`)
- Inconsistent city names (`"newyork"`, `"NY"`, `"Nwe Yrok"`)
- Missing Patient IDs and missing values across multiple columns
- Duplicate patient entries
- Emoji characters in notes fields

### Limitations

- Dataset may not represent all geographical regions or patient demographics
- Some fields contain missing or incomplete information
- Limited variables for advanced predictive modelling

---

## ETL & Data Cleaning

The ETL pipeline was implemented across five Jupyter Notebooks and an automated `etl_pipeline.py` script.

### Notebook Execution Order

```
01_extraction.ipynb       → Raw data loading and initial inspection
02_cleaning.ipynb         → Data cleaning and standardisation
03_eda.ipynb              → Exploratory data analysis
04_statistical_analysis.ipynb → Statistical testing and correlation
05_final_load_prep.ipynb  → Final dataset preparation and export
```

### Cleaning Steps Applied

1. **Age standardisation** — Converted text ages (`"twenty"` → `50`) and replaced invalid values (`-5`, `250`) with median imputation
2. **BMI normalisation** — Stripped unit suffixes (`"22kg/m2"` → `22.0`) and converted to float
3. **Blood pressure parsing** — Extracted systolic and diastolic values from all format variants into separate `systolic_bp` and `diastolic_bp` columns
4. **Heart rate correction** — Converted text values (`"eighty"` → `80`) and replaced outliers (`0`, `500`) with median values
5. **Gender standardisation** — Mapped all variants to `male`, `female`, `unknown`
6. **City normalisation** — Standardised city names to lowercase canonical forms (`"Nwe Yrok"` → `"new york"`, `"la"` → `"los angeles"`)
7. **Smoker status standardisation** — Mapped `"EX-smoker"`, `"Former"`, `"yes"`, `"No"`, `"n/a"` to consistent categories
8. **Date standardisation** — Parsed multiple date formats (`"Apr 15 2021"`, `"20210415"`, `"15/04/2021"`) to ISO format
9. **Diagnosis code cleaning** — Standardised unknown/missing codes to `"UNKNOWN"`
10. **Duplicate removal** — Identified and removed duplicate patient records
11. **Missing value handling** — Applied median/mode imputation for numerical and categorical columns respectively

### Output

Cleaned dataset saved to: `data/processed/cleaned_data.csv`

---

## KPIs & Metrics

Key Performance Indicators were defined to measure healthcare performance and support decision-making.

| KPI | Description |
|---|---|
| Patient Recovery Rate | Percentage of patients with `has_disease = 0` (no active disease) |
| Average Treatment Duration | Mean follow-up interval across patient cohorts |
| Condition Distribution | Prevalence of ICD diagnosis codes across the population |
| Demographic Analysis | Disease and treatment trends across age groups and gender |
| Cholesterol Risk Rate | Proportion of patients with high cholesterol levels |
| Hypertension Prevalence | Proportion of patients with elevated systolic BP (>130 mmHg) |
| Diabetes Rate | Proportion of diabetic patients in the dataset |

---

## Exploratory Data Analysis (EDA)

EDA was performed to identify patterns, trends, and anomalies in the cleaned dataset.

### Key Analyses Conducted

- **Age distribution** — Histogram of patient ages to identify the most represented age groups
- **Gender distribution** — Bar chart of male vs. female vs. unknown patients
- **City distribution** — Frequency of patients across New York, Chicago, Los Angeles, Boston
- **Diagnosis code frequency** — Distribution of ICD codes (A00, B20, E11.9, I10, UNKNOWN)
- **BMI distribution** — Box plot to identify underweight, normal, overweight, and obese patients
- **Cholesterol levels** — Distribution across normal, 190, 240, 250 mg/dL categories
- **Smoking status** — Breakdown of smoker, non-smoker, former smoker, unknown
- **Disease prevalence** — Proportion of `has_disease = 1` vs. `has_disease = 0`
- **Follow-up intervals** — Distribution of 14-day, 30-day, and N/A follow-up schedules
- **Outlier detection** — Box plots for heart rate, BMI, and blood pressure

### Key Insights from EDA

- Certain age groups show higher susceptibility to specific conditions (e.g., hypertension in older patients)
- Gender distribution is relatively balanced, with a notable proportion of unknown gender entries in the raw data
- New York and Chicago are the most represented cities in the dataset
- Diagnosis code I10 (hypertension) and E11.9 (type 2 diabetes) are among the most frequent conditions
- A significant proportion of patients have high cholesterol levels (≥240 mg/dL)
- Smokers and former smokers show higher rates of cardiovascular-related diagnoses
- Outliers in heart rate and blood pressure were concentrated in uncleaned records

Visualisations used: bar charts, histograms, box plots, pie charts, and heatmaps.

---

## Statistical Analysis

Statistical analysis was conducted to uncover deeper relationships within the data.

### Methods Used

- **Correlation analysis** — Pearson correlation matrix across numerical variables (age, BMI, heart rate, systolic BP, diastolic BP, cholesterol)
- **Regression analysis** — Linear regression to understand predictive relationships between age, BMI, and disease presence
- **Hypothesis testing** — Chi-square tests to validate significant differences in disease rates across demographic groups
- **Group comparison** — Mean comparison of clinical indicators (BP, cholesterol, BMI) across diabetic vs. non-diabetic patients

### Key Findings

- Strong positive correlation observed between age and systolic blood pressure
- BMI shows moderate correlation with cholesterol levels and disease presence
- Diabetic patients exhibit statistically significantly higher cholesterol and BMI values compared to non-diabetic patients
- Smoking status shows a statistically significant association with hypertension diagnosis (I10)
- Certain treatments (Lisinopril/Metformin combination) are more frequently associated with diabetic and hypertensive patients, suggesting appropriate clinical targeting

---

## Key Insights

1. Patients in older age groups are more vulnerable to hypertension (I10) and type 2 diabetes (E11.9)
2. Treatment effectiveness varies significantly across patient segments — Lisinopril/Metformin is predominantly prescribed for diabetic and hypertensive patients
3. Hypertension (I10) and type 2 diabetes (E11.9) show the highest prevalence among the diagnosed conditions
4. Recovery rates are influenced by both demographic factors (age, BMI) and treatment adherence (follow-up intervals)
5. Patients with high BMI (>30) consistently show higher rates of disease presence
6. Smokers and former smokers have disproportionately higher rates of cardiovascular diagnoses
7. High-risk groups can be identified using a combination of age, BMI, smoking status, and cholesterol level
8. Preventive healthcare strategies targeting high-BMI and smoking populations could significantly reduce condition severity
9. Data highlights inefficiencies in follow-up scheduling — a large proportion of records have no follow-up date recorded
10. Certain cities (New York, Chicago) show higher patient volumes, suggesting potential resource allocation opportunities

---

## Tableau Dashboard

An interactive Tableau dashboard was developed to allow stakeholders to explore key metrics dynamically.

### Dashboard Features

- Patient distribution by city and demographic group
- Condition prevalence by diagnosis code
- Treatment type breakdown across patient segments
- Disease rate by age group and gender
- KPI summary cards for recovery rate, average follow-up, and condition counts
- Filters for city, gender, smoking status, and diagnosis code

Dashboard screenshots are stored in: `tableau/screenshots/`

---

## Business Recommendations

1. **Focus healthcare resources on high-risk demographic groups** — Older patients and those with high BMI should receive priority screening for hypertension and diabetes
2. **Optimise treatment strategies** — Lisinopril/Metformin combinations show strong alignment with diabetic and hypertensive patient profiles; standardise prescribing guidelines accordingly
3. **Implement preventive care programs** — Target smoking cessation and weight management programs at identified high-risk segments
4. **Improve data collection processes** — Standardise data entry for age, BMI, blood pressure, and follow-up dates to reduce preprocessing overhead in future cycles
5. **Use data-driven insights for resource allocation** — Cities with higher patient volumes (New York, Chicago) may require additional healthcare capacity
6. **Enforce follow-up scheduling** — A significant proportion of patients have no follow-up date; implementing mandatory follow-up scheduling could improve outcome tracking

---

## Limitations & Future Scope

### Limitations

- Dataset may not represent all geographical regions or patient demographics
- Missing values and data entry inconsistencies required significant imputation, which may affect accuracy
- Limited variables available for advanced predictive modelling (no lab results, treatment outcomes, or longitudinal data)
- Anonymised patient names reduce the ability to track individual patient journeys

### Future Scope

- Apply machine learning models (logistic regression, random forest) for disease prediction
- Integrate real-time healthcare data streams for live dashboard updates
- Expand dataset to include broader geographic coverage and additional clinical variables
- Develop an automated reporting pipeline for periodic analytics delivery
- Build a patient risk scoring model using demographic and clinical indicators

---

## Technologies Used

| Technology | Purpose |
|---|---|
| Python 3 | Core programming language |
| Pandas 2.2.2 | Data manipulation and cleaning |
| NumPy 1.26.4 | Numerical computations |
| Matplotlib 3.9.0 | Data visualisation |
| SciPy 1.13.1 | Statistical analysis |
| Scikit-learn 1.5.0 | Feature engineering and regression |
| Jupyter Notebook 7.2.0 | Interactive analysis environment |
| OpenPyXL 3.1.5 | Excel file handling |
| Tableau | Interactive dashboard development |

---

## Project Structure

```
Health_VAASS_CuraMind/
│
├── data/
│   ├── raw/
│   │   └── Patient_Health_Records_Raw.csv
│   └── processed/
│       ├── extracted_data.csv
│       └── cleaned_data.csv
│
├── notebooks/
│   ├── 01_extraction.ipynb
│   ├── 02_cleaning.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_statistical_analysis.ipynb
│   └── 05_final_load_prep.ipynb
│
├── scripts/
│   └── etl_pipeline.py
│
├── tableau/
│   └── screenshots/
│
├── requirements.txt
├── README.md
└── REPORT.md
```

---

*Report prepared by Shorya Taneja | Health VAASS CuraMind | Newton School of Technology | April 2026*
