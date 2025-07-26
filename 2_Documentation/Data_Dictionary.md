# Data Dictionary: AI Diabetes Prediction Model

This document outlines the data schemas for all sources and generated outputs used in the Power BI report.

**Last Updated:** 23-July-2025

---

## Source 1: Model Training Data

This is the historical data used to train the machine learning models inside the Python script.

* **File:** `diabetes_enhanced_data.csv`
* **Description:** A dataset containing patient clinical features and diagnosed outcomes.

| Column Name | Data Type | Description | Role |
| :--- | :--- | :--- | :--- |
| `Patient_ID` | Integer | Unique identifier for each patient. | Identifier |
| `Age` | Integer | Patient's age in years. | Feature |
| `BMI` | Decimal | Body Mass Index (kg/m²). | Feature |
| `HbA1c` | Decimal | Glycated Hemoglobin (%). | Feature |
| `Fasting_Glucose`| Decimal | Blood glucose level (mg/dL) after fasting. | Feature |
| `Family_History` | Binary | 1 if patient has a family history of diabetes, 0 otherwise. | Feature |
| `Hypertension` | Binary | 1 if patient has hypertension, 0 otherwise. | Feature |
| `Is_Pregnant` | Binary | 1 if the patient is pregnant, 0 otherwise. | Feature |
| `Kidney_Function`| Text | Categorical state of kidney health ('Normal', 'Mild', 'Severe'). | Feature |
| `Diabetes_Status`| Binary | 1 if the patient is diabetic, 0 otherwise. | Target |
| `Diabetes_Type` | Text | The diagnosed type of diabetes ('Type 1', 'Type 2', 'Gestational'). | Target |
| `Recommended_Treatment` | Text | The treatment prescribed in the historical data. | Target |

---

## Source 2: Treatment Details

This source provides additional context for the recommended treatments.

* **File:** `Treatment_Details.xlsx` (Assumed name)
* **Description:** An Excel sheet that provides detailed descriptions for each treatment type.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Treatment` | Text | The name of the treatment. Primary key for joining. |
| `Description` | Text | A detailed explanation of the treatment protocol. |
| `Category` | Text | The class of treatment (e.g., 'Medication', 'Lifestyle'). |

---

## Generated Output Columns (from Python Script)

These columns are created in real-time by the Python script and form the final output table used in the visuals.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Diagnosis` | Text | The model's prediction of whether the patient is 'Diabetic' or 'Not Diabetic'. |
| `Diagnosis_Confidence`| Decimal | The model's confidence (probability) in the `Diagnosis` prediction. |
| `Diabetes_Type` | Text | The model's prediction of the diabetes type. Returns 'N/A' if not diabetic. |
| `Treatment` | Text | The model's final treatment recommendation. |