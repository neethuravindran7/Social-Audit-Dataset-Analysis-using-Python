# 📊 Social Audit Dataset Analysis 

## 📘 1. Project Introduction
The Social Audit is a powerful tool to ensure transparency, accountability, and citizen participation in government welfare schemes like MGNREGA.
This project aims to analyze the Social Audit dataset to track financial misappropriation and recovery across different states and Gram Panchayats.

## 🎯 2. Project Objectives
1. To clean and preprocess raw social audit data
2. To identify and calculate Pending Recovery Amount (Misappropriation - Recovery)
3. To detect inconsistencies and outliers in financial data

## 📂 3. Dataset Overview
- Source:https://docs.google.com/spreadsheets/d/1qeLiHEr79YUZWO_apHufcUJfi-aE-1Xo/edit?usp=sharing&ouid=112658906127213146931&rtpof=true&sd=true
- Format :csv
- Original Size: 2000 Rows x 21 Columns
- After Cleaning: 1916 Rows x 20 Columns
- Duplicates Removed: 84 Rows

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

## 🧹 4. Phase 1 - Data Cleaning Steps 
- Checked shape, info, null values, duplicates (84 found)
- Removed duplicates -> 1916 rows
- Dropped Audit_Date column (not needed for analysis)
- Added Pending_Recovery column for analysis
- Checked inconsistencies using unique() - all values standardized
- Outlier Checking using Boxplot

## 5. Phase 2 - Key Insights & Visualizations  (Editing)

#### 1. State-wise Complaints Analysis
- Tamil Nadu - Highest complaints: 263
- Telangana, Andhra Pradesh follow
- Plot: sns.barplot(palette='Purples_r')

#### 2. State-wise Mandays Generated
- Tamil Nadu - Max Mandays: 10,81,873
- Karnataka, AP high generation
- Plot: Horizontal bar with dark purple theme

#### 3. Correlation Heatmap
- High correlation between Total_Expenditure and Misappropriation_Amount (0.88)
- Misappropriation_Amount vs Recovery_Amount positively correlated
- Plot: sns.heatmap(cmap='Purples', annot=True)

#### 4. Financial Analysis
- Total Misappropriation identified state-wise
- Recovery Rate calculated: (Recovery / Misappropriation)*100
- Pending Recovery = Misappropriation - Recovery

### Findings from EDA
- Tamil Nadu leads in both complaints and mandays - indicates active social audit process
- Financial irregularities mostly in Wages_Paid and Material_Cost
- Recovery rate varies across states - scope for improvement

## 🔍 6. Phase 3 - Insight Generation and Report 
### 📈 Exploratory Data Analysis

### 🔍 Key Insights

*1. Scheme-wise Total Misappropriation *
- PMAY-G highest fraud ∼2.95 Cr
- SBM-G lowest ∼2.42 Cr
- PMAY-G housing scheme most vulnerable

*2. Univariate Analysis*
- Misappropriation Amount: 0 to 1.49L, Mean 68,748, Median 67,696. Peak at 0-5k range (240 cases), but uniform till 1.4L - fraud at all levels
- *Audit Status:* Under Review 21.1% (405) highest, Closed 20.9% (400), ATR Pending 20.9% (400), Pending Recovery 19.1% (365), Completed 18.1% (346) lowest - only 18% audits completed
- *Total Expenditure :* Median ∼1.0L, Q1 0.55L, Q3 1.45L, Range 0-2L, No outliers - fairly distributed[Boxplot]

*3. Bivariate Analysis*
- *Scheme vs Fraud:* PMAY-G 2.95 Cr > MGNREGA 2.65 Cr > PMGSY 2.50 Cr > NSAP 2.53 Cr > SBM-G 2.42 Cr
- *Expenditure vs Misappropriation :* No correlation, random distribution. Fraud independent of expenditure. All audit statuses mixed uniformly[Scatter]

*4. Groupby - District-wise Misappropriation*
- Udaipur highest total fraud 89,54,404 (118 cases)
- Chennai highest fraud cases 133, but avg low 66,629 - frequent small frauds
- Gaya highest avg fraud per case 77,300 - high-value frauds
- Top 8 districts uniform 86L - 89L range

*5. Pivot Table - District vs Audit_Status*
- Fraud distributed across all audit stages
- Audit status independent of district
- No concentration in single stage

*6. Correlation Heatmap - Multivariate*
- Misappropriation vs Pending_Recovery = *0.88 strong positive* - pending directly linked to fraud
- Recovery vs Pending_Recovery = -0.46 negative - as pending increases, recovery decreases
- All other variables correlation near 0 - independent

### 💡 SUGGESTIONS AND RECOMMENDATIONS

1. Immediate Action on PMAY-G Scheme:
PMAY-G has the highest total misappropriation of ₹2.95 Crores, which is 21.9% higher than SBM-G. Since this scheme involves material procurement like cement, steel, and bricks, implement mandatory geo-tagged material bills with third-party verification. Make 100% social audit compulsory for PMAY-G.

2. Fix the Pending Audit Status:
60.9% of audits are still pending - Under Review 21.1%, ATR Pending 20.9%, and Pending Recovery 19.1%. Only 39% are closed or completed. Introduce a strict 30-day deadline for Action Taken Report submission with auto-redirection to BDO and District Collector.

3. Equal Audit for All Work Sizes:
Correlation between Total Expenditure and Misappropriation is only 0.01, meaning fraud does not depend on budget size. A small work of ₹50,000 can have ₹1.4 Lakhs fraud while a large work of ₹20 Lakhs can have zero fraud. Implement random sampling audit for all sizes.

4. Strengthen Recovery Mechanism:
Misappropriation vs Pending Recovery has a strong positive correlation of 0.88, and Recovery vs Pending has a negative correlation of -0.46. To improve recovery, link pending recovery with the next fund release for the Gram Panchayat. Apply rule: No recovery, No next installment.

5. Focus on High Material Cost Works & Replicate Best Practices:
Road Construction has the highest material cost of ₹14.97 Crores and Pond Desilting ₹14.79 Crores, making them high-risk for misappropriation. Prioritize audits on these infrastructure works with strict physical measurement verification. Study Tamil Nadu's model (10.81 Lakhs mandays with uniform complaints) and replicate it in low-mandays states like Bihar (9.01 Lakhs).


### 📌 CONCLUSION - Social Audit Project
Analysis of social audit records under MGNREGA and allied schemes identifies expenditure patterns, misappropriation trends, scheme-wise vulnerabilities, state-wise fraud distribution, and audit status gaps also shows that the social audit system is effective in detection but weak in closure. Strengthening recovery, ensuring timely audit closure, and focusing on material-intensive works like Roads and Ponds will improve the mandays for workers and impact on economic growth of states.

### 📊 Key Stats from Analysis
- Highest Material Cost: Road Construction - ₹14.97 Crores (₹149,759,647)
- Second Highest: Pond Desilting - ₹14.79 Crores
- Lowest in Top 5: Toilet Construction - ₹11.92 Crores (small-scale structure)
- Final Dataset: 1916 entries, 20 columns, 0 null values

## 🛠️ Tools
Python, Pandas, NumPy, Matplotlib, Seaborn, GitHub

## 👩‍💻 Author
Neethu P 
