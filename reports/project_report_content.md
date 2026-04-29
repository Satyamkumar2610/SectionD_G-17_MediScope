# MediScope: Transforming Raw Patient Datasets into Actionable Healthcare Insights
## Final Project Report

**Sector:** Healthcare Analytics  
**Date:** April 2026  

---

## 1. Executive Summary
Hospitals generate thousands of data points per patient daily, yet clinical and administrative teams often lack the tools to synthesize this raw data into actionable operational strategies. MediScope was developed to bridge this gap by analyzing an intensive care dataset of over 76,000 lab records. This report details the transformation of raw clinical data into a decision-support framework that identifies operational bottlenecks and clinical risks. 

Our analysis reveals that Emergency admissions account for 91% of patient volume and drive a 36% increase in Length of Stay (LOS). Furthermore, nearly 40% of all laboratory tests return abnormal results, with Hematology emerging as a primary source of operational strain. By implementing targeted triage protocols, gender-specific reference ranges, and stricter testing guidelines, hospital administration can expect significant reductions in LOS and testing overhead.

## 2. Problem Statement
Hospital resources—specifically ICU bed availability and laboratory processing capacity—are finite and highly expensive. The facility faces severe bottlenecks in patient flow, driven by extended hospital stays and high volumes of laboratory testing. The core problem lies in the inability to identify which patient sub-populations and clinical departments are disproportionately driving these inefficiencies. Without data-driven visibility into admission types, demographic risk profiles, and testing patterns, the hospital cannot proactively allocate resources or optimize clinical workflows.

## 3. Dataset Description
The analysis was performed on a de-identified Intensive Care Unit (ICU) dataset consisting of 76,069 laboratory records.

*   **Total Patients:** 100
*   **Total Lab Tests:** 76,069
*   **Key Variables:**
    *   `admission_type`: Emergency, Elective, Urgent
    *   `los_days`: Length of Stay in days
    *   `is_abnormal`: Binary indicator for abnormal test results
    *   `category`: Clinical laboratory department (e.g., Hematology, Chemistry)
    *   `gender` & `dob`: Demographic markers for age and sex analysis

## 4. Data Cleaning & ETL Process (Python-based)
A robust Python ETL (Extract, Transform, Load) pipeline was engineered using `pandas` to prepare the data for analysis.
*   **Extraction:** Raw tables (`LABEVENTS`, `ADMISSIONS`, `PATIENTS`, `D_LABITEMS`) were ingested from flat files.
*   **Transformation:**
    *   *Null Handling:* 5 records with unresolvable null values in critical clinical fields were dropped to maintain statistical integrity.
    *   *Feature Engineering:* `los_days` was calculated from admission and discharge timestamps. `is_abnormal` was derived from text-based flag columns.
    *   *Joins:* Disparate tables were merged on `subject_id` and `hadm_id` to create a unified, patient-centric master record (`clean_lab_master_v3.csv`).
*   **Load:** The cleaned master dataset was exported, followed by aggregations into Tableau-ready subset files to ensure dashboard performance.

## 5. KPI Framework
To establish a baseline for operational health, we tracked four primary Key Performance Indicators (KPIs):
*   **Total Laboratory Tests:** 76,069
*   **Tests per Patient:** ~760
*   **Overall Abnormal Rate:** 39.1%
*   **Average Length of Stay (LOS):** ~22.5 days

## 6. Exploratory Data Analysis (EDA)
EDA focused on understanding the distribution of risk and resources. We identified that the patient population is highly acute, evidenced by the 39.1% abnormal rate. When breaking down volume, Emergency admissions vastly outnumbered Elective and Urgent care. Furthermore, volume spikes were observed across specific months, prompting an investigation into testing efficiency.

## 7. Statistical Analysis
To ensure insights were not merely coincidental, we applied rigorous statistical testing:
*   **Hypothesis Testing (Independent T-Test):** We tested the variance in LOS between Emergency and Elective admissions. The result was highly significant (p < 0.0001), proving that Emergency admissions systematically cause longer stays.
*   **Chi-Square Test of Independence:** We tested the relationship between Gender and Abnormal flags. The result (p < 0.0001) confirmed that Female patients have a statistically higher rate of abnormal results compared to Males.
*   **Correlation Analysis:** A moderate positive correlation was established between the frequency of abnormal tests and total LOS, indicating that clinical severity directly drives operational bottlenecks.

## 8. Dashboard Explanation (Tableau)
The Tableau dashboard was designed as an executive decision-support tool. It moves from macro to micro insights:
*   **Top Row (Macro):** Displays the core KPI framework (Total Patients, Tests, Abnormal Rate).
*   **Middle Row (Demographic/Operational):** Features a 100% Stacked Bar Chart highlighting the gender risk disparity and a Box Plot illustrating the severe LOS jump for Emergency patients.
*   **Bottom Row (Clinical Deep Dive):** Uses a Quadrant Scatter Plot to isolate specific departments (like Hematology) that drive high testing volumes alongside high abnormal rates.

## 9. Key Insights
1.  **High Clinical Risk Baseline:** Nearly 40% (39.1%) of all lab tests flag as abnormal, indicating a highly acute patient population that requires intense clinical monitoring.
2.  **Emergency Admission Dominance:** Emergency admissions account for approximately 91% of total patient volume, creating massive strain on unpredictable resource allocation.
3.  **The LOS Bottleneck:** Emergency patients experience a 36% longer length of stay (averaging 29 days) compared to elective patients (21 days), making them the primary driver of bed shortages.
4.  **Gender Risk Disparity:** Female patients show consistently higher abnormal lab rates across all admission types, indicating potential issues with universal clinical reference ranges.
5.  **The Hematology Drain:** Hematology tests represent both the highest volume of tests and the highest abnormal rate, acting as a major operational and financial bottleneck.
6.  **Routine Over-Testing:** Time-series analysis shows that while overall test volumes spike during certain periods, the abnormality rate remains flat. This indicates routine over-testing that yields no new clinical value.
7.  **Acuity Drives Stays:** There is a moderate positive correlation between the frequency of abnormal tests a patient receives and their total LOS, linking clinical severity directly to operational cost.
8.  **Testing Density:** The average ICU patient receives approximately 760 lab tests during their stay, representing a massive processing burden on the laboratory department.

## 10. Business Recommendations & Estimated Impact
Based on the data, we recommend the following strategic interventions:

1.  **Optimize Triage Workflows to Reduce Emergency LOS**
    *   *Action:* Implement fast-track protocols for non-critical emergency admits and dedicate specific bed blocks for predictable elective recoveries.
    *   *Estimated Impact:* A 10% reduction in Emergency LOS could save approximately 2.9 bed-days per patient, massively increasing overall hospital capacity and revenue generation.
2.  **Introduce Gender-Specific Lab Baselines**
    *   *Action:* Audit and adjust the `D_LABITEMS` reference ranges to account for statistical variances in female baselines.
    *   *Estimated Impact:* Expected to reduce "false positive" abnormal alerts by 5-10%, reducing alert fatigue among clinical staff and saving physician review time.
3.  **Implement Stricter Testing Protocols for Hematology**
    *   *Action:* Introduce "hard stops" or mandatory physician overrides in the EHR system for repeat hematology orders within a 24-hour window unless clinically justified.
    *   *Estimated Impact:* Projected to reduce overall testing volume spikes by 15%, resulting in direct savings in laboratory reagents, equipment wear, and technician hours.

## 11. Limitations & Future Scope
**Limitations:** The dataset is restricted to 100 patients, which limits the generalizability of the findings across a wider hospital network. Furthermore, the lack of direct financial data (cost per test, cost per bed day) means financial impacts must be estimated rather than calculated precisely.
**Future Scope:** Future iterations should integrate financial datasets to perform exact Cost-Benefit Analyses. Additionally, expanding the dataset to thousands of patients would allow for the deployment of Machine Learning models to predict a patient's LOS on the exact day of admission.
