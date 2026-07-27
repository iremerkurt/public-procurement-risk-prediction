# 📊 Public Procurement Risk Analysis and Risk Level Prediction

## 📌 Project Overview

This project presents an end-to-end machine learning pipeline for analyzing public procurement data and predicting procurement risk levels.

The main objective is to analyze public tender processes, identify potential risk factors, and classify tenders into different risk categories using machine learning techniques.

The project uses the **Global Public Procurement Dataset (GPPD)**. Due to the large size of the dataset, procurement records belonging to **Germany** were selected for analysis.

Each procurement record is classified into one of three risk categories:

- Low Risk
- Medium Risk
- High Risk

The project covers the complete machine learning workflow:

- Data preprocessing
- Exploratory Data Analysis (EDA)
- Missing value handling
- Outlier analysis
- Feature engineering
- Risk score creation
- Feature selection
- Machine learning data preparation


---

# 🎯 Project Objective

The main objectives of this project are:

- Analyze risk factors in public procurement processes,
- Investigate the impact of competition, duration, and price-related variables,
- Create meaningful risk indicators,
- Develop a machine learning pipeline for predicting procurement risk levels.


The prediction process is based on:

- Competition characteristics,
- Bid information,
- Tender process durations,
- Price-related features,
- Procurement risk indicators.


---

# 📂 Dataset Description

The project uses the:

**Global Public Procurement Dataset (GPPD)**


The dataset contains detailed information about public procurement processes, including:

- Tender procedure types,
- Supply types,
- Buyer information,
- Bid counts,
- Procurement dates,
- Estimated and final prices,
- Risk-related indicators.


Due to the large size of the original dataset, only **Germany procurement records** were used in this project.

The raw dataset is not included in this repository because of storage limitations.


---

# ⚙️ 1. Environment Setup

The execution environment was prepared and required Python libraries were imported.

Google Drive was connected to access large-scale dataset files.

Main libraries used:

- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly


The purpose of this stage was:

- Preparing the data analysis environment,
- Enabling large dataset processing,
- Creating the required infrastructure for analysis and modeling.


---

# 💾 2. Dataset Loading and Initial Validation

In this stage, the procurement dataset was loaded and initial validation steps were performed.

Performed operations:

- Loading the dataset,
- Checking dataset dimensions,
- Reviewing column names,
- Examining data types,
- Inspecting initial records.


This step helped understand the dataset structure and identify relevant variables for further analysis.


---

# 🔍 3. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the overall structure and characteristics of the dataset.

The following analyses were conducted:

- Statistical analysis of numerical variables,
- Analysis of categorical variables,
- Missing value investigation,
- Feature distribution analysis,
- Correlation analysis.


Techniques used:

- Descriptive statistics,
- Missing value analysis,
- Pearson correlation matrix,
- Data visualization.


The purpose of this stage was to identify important patterns, data quality issues, and relationships between variables.


## 📊 Visualization Results

### Missing Value Analysis

![Missing Value Analysis](results/figures/missing_value_analysis.png)


### Data Type Distribution

![Data Type Distribution](results/figures/data_type_distribution.png)


### Pearson Correlation Matrix

![Pearson Correlation Matrix](results/figures/pearson_correlation_matrix.png)


### Numeric Feature Outlier Analysis

![Numeric Outlier Analysis](results/figures/numeric_outlier_analysis.png)


### Risk Level Distribution

![Risk Level Distribution](results/figures/risk_level_distribution.png)


### Risk Indicator Count Distribution

![Risk Indicator Count Distribution](results/figures/risk_indicator_count_distribution.png)


### Bid Count Distribution by Risk Level

![Bid Count Distribution by Risk Level](results/figures/bid_count_distribution_by_risk_level.png)


---

# 🧹 4. Data Preprocessing

The raw dataset was cleaned and transformed into a suitable format for further analysis and modeling.

Performed operations:

- Removing unnecessary columns,
- Removing variables with extremely high missing ratios,
- Correcting data types,
- Converting date columns into datetime format.


New time-based features were created:

- Submission period,
- Decision period,
- Decision duration days,
- Total process duration.


The purpose of this stage was to improve data quality and prepare the dataset for feature engineering.


---

# ⚙️ 5. Missing Value Handling

Missing values were analyzed and handled using appropriate preprocessing techniques.

Performed operations:

- Calculating missing value percentages,
- Evaluating highly missing columns,
- Removing irrelevant missing features,
- Applying suitable imputation strategies.


For numerical variables:

- Missing values were handled using median imputation.


For categorical variables:

- Missing values were filled using the most frequent category.


---

# 📦 6. Outlier Analysis and Transformation

Numerical variables were analyzed to detect potential outliers and extreme values.

Special attention was given to:

- Tender prices,
- Bid counts,
- Duration variables.


Highly skewed variables were transformed using:

**Log1p transformation**


Applied transformations include:

- tender_estimatedprice,
- tender_finalprice,
- decision_duration_days,
- submission_period,
- tender_recordedbidscount.


The goal was to reduce the impact of extreme values and improve model performance.


---

# ⚙️ 7. Feature Engineering

New meaningful features were created from raw procurement variables.


## Competition Features

### low_competition

Identifies tenders with a low level of competition based on bid information.


### has_bids

Indicates whether a tender received any bids.


## Time-Based Features

Created variables:

- submission_period,
- decision_period,
- decision_duration_days,
- total_process_duration.


These features represent the duration characteristics of procurement processes.


---

# 🚩 Risk Score and Risk Level Creation

The target variable used for machine learning:

```
risk_level
```

was created based on procurement risk indicators.


Risk indicators used:

- corr_nocft,
- corr_proc,
- corr_decp,
- corr_singleb,
- corr_subm,
- corr_buyer_concentration,
- corr_tax_haven.


The total number of risk indicators was calculated as:

```
risk_indicator_count
```


Risk categories were generated as follows:


| Risk Indicator Count | Risk Level |
|---|---|
| 0-1 | Low Risk |
| 2 | Medium Risk |
| 3+ | High Risk |


To prevent data leakage, risk indicator variables used to generate the target variable were excluded from model input features.


---

# 🎯 8. Feature Selection

Feature selection was performed to determine the most informative variables for machine learning models.

Objectives:

- Remove redundant features,
- Reduce unnecessary complexity,
- Improve model efficiency,
- Select meaningful predictors.


Performed operations:

- Correlation analysis,
- Feature evaluation,
- Removal of target-related risk variables.


---

# 🤖 9. Machine Learning Data Preparation

Selected features were prepared for machine learning algorithms.


## Numerical Features

Applied preprocessing:

- Missing value imputation,
- Feature scaling.


## Categorical Features

Applied preprocessing:

- Missing value imputation,
- One-Hot Encoding.


## Target Encoding

The target variable:

- Low Risk,
- Medium Risk,
- High Risk

was transformed into numerical labels using **LabelEncoder**.


## Train-Test Split

The dataset was divided into:

- 80% Training Data,
- 20% Testing Data.


The `stratify` parameter was used to preserve class distribution between training and testing datasets.


---

# 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly
- Google Colab


---

# 📁 Project Structure

```
Ihale-Risk-Tahmini/

│
├── ihale_risk_prediction.ipynb
├── README.md
├── requirements.txt
│
└── results/
    └── figures/
        ├── missing_value_analysis.png
        ├── data_type_distribution.png
        ├── pearson_correlation_matrix.png
        ├── numeric_outlier_analysis.png
        ├── risk_level_distribution.png
        ├── risk_indicator_count_distribution.png
        └── bid_count_distribution_by_risk_level.png
```


---

# 📌 Conclusion

This project analyzed public procurement data, created meaningful risk-related features, and prepared a complete machine learning pipeline for procurement risk prediction.

The developed pipeline provides a foundation for training machine learning models that can classify procurement processes into different risk categories based on historical tender characteristics.
