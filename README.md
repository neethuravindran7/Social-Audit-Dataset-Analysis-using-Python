# 📊 Social Audit Dataset Analysis using Python
### Internship Project - Phase 1 Completed ✅

## 📘 1. Project Introduction
The Social Audit is a powerful tool to ensure transparency, accountability, and citizen participation in government welfare schemes like MGNREGA.
This project aims to analyze the Social Audit dataset to track financial misappropriation and recovery across different states and Gram Panchayats.

## 🎯 2. Project Objectives
1. To clean and preprocess raw social audit data
2. To identify and calculate Pending Recovery Amount (Misappropriation - Recovery)
3. To detect inconsistencies and outliers in financial data
4. To prepare data for Phase 2 - EDA and Visualization

## 📂 3. Dataset Overview
- Original: 2000 Rows x 21 Columns
- After Cleaning: 1916 Rows x 20 Columns
- Duplicates Removed: 84 Rows
- Missing Values: 0
- Memory: 314.3+ KB

### Column Description
| Column | Description |
| :--- | :--- |
| State, District, Gram_Panchayat | Location details |
| Financial_Year | 
| Scheme_Name, Work_Type | 
| Audited_By |
| Total_Expenditure |
| Misappropriation_Amount | 
| Recovery_Amount | 
| Issues_Found, Issue_Type | 
| Audit_Status, Action_Taken |
| Beneficiaries_Covered |
| Wages_Paid, Material_Cost | 
| Complaints_Received | Complaints count |+
|Action_Taken|
| Pending_Recovery | Calculated = Misappropriation - Recovery |

## 🧹 4. Phase 1 - Data Cleaning Steps (Completed)
- Checked shape, info, null values, duplicates (84 found)
- Removed duplicates -> 1916 rows
- Dropped Audit_Date column (not needed for analysis)
- Added Pending_Recovery column for analysis
- Checked inconsistencies using unique() - all values standardized
- Outlier Checking using Boxplot

Final Dataset: 1916 entries, 20 columns, 0 null values - Ready for EDA

## 👩‍💻 Author
Neethu P - Data Analytics Intern

## 🛠️ Tech Stack
Python, Pandas, NumPy, Matplotlib, Seaborn, GitHub
