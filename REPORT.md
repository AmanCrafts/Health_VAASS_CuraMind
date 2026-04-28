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
