# Health_VAASS_CuraMind

## Project Overview

CuraMind is a healthcare analytics capstone project built using raw patient health record data. The project focuses on extracting insights from healthcare data through data cleaning, preprocessing, exploratory data analysis (EDA), statistical analysis, and predictive analytics workflows.

---

# Project Structure

```plaintext
Health_VAASS_CuraMind/
│
├── data/
│   ├── raw/
│   └── processed/
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
├── reports/
│
├── docs/
│
├── requirements.txt
└── README.md
```

---

# Dataset Setup

1. Download the dataset.
2. Place the dataset inside:

```plaintext
data/raw/
```

3. Rename the dataset file to:

```plaintext
patient_health_data.csv
```

---

# Environment Setup

## Step 1 — Navigate to the project directory

```bash
cd Health_VAASS_CuraMind/
```

---

## Step 2 — Create a virtual environment

### Mac/Linux

```bash
python3 -m venv venv
```

### Windows

```bash
python -m venv venv
```

---

## Step 3 — Activate the virtual environment

### Mac/Linux

```bash
source venv/bin/activate
```

### Windows CMD

```bash
venv\Scripts\activate
```

### Windows PowerShell

```powershell
.\venv\Scripts\Activate.ps1
```

---

## Step 4 — Install dependencies

```bash
pip install -r requirements.txt
```

---

## Step 5 — Register Jupyter kernel

```bash
python -m ipykernel install --user --name=curamind_env
```

---

# Running the Project

## Start Jupyter Notebook

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

---

# Notebook Execution Order

Run the notebooks in the following order:

```plaintext
1. 01_extraction.ipynb
2. 02_cleaning.ipynb
3. 03_eda.ipynb
4. 04_statistical_analysis.ipynb
5. 05_final_load_prep.ipynb
```

---

# Running the ETL Pipeline

Execute the ETL pipeline using:

```bash
python scripts/etl_pipeline.py
```

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* SciPy
* Scikit-learn
* Jupyter Notebook

---

# Features

* Raw healthcare data extraction
* Data cleaning and preprocessing
* Exploratory data analysis
* Statistical analysis
* Feature engineering
* ETL pipeline automation
* Predictive healthcare analytics preparation

---

# Team Notes

* Ensure the virtual environment is activated before running notebooks.
* Keep raw datasets unchanged inside the `data/raw/` directory.
* Store processed datasets inside `data/processed/`.

---

# Future Enhancements

* Machine learning model integration
* Patient risk prediction
* Dashboard visualization using Tableau
* Automated reporting pipeline
* Real-time healthcare analytics

---