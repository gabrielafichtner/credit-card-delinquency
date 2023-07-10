# Predicting Credit Card Delinquency

## Project Description

This project aims at building a predictive model to anticipate credit card delinquency, a crucial risk management technique in the financial industry. By analyzing personal information and historical credit-related data of cardholders, we can estimate the likelihood of future payment defaults and implement efficient risk control measures. The project utilizes two datasets: one containing application data with crucial client information and the other focusing on credit card details.

## Data Overview

- **Application Data**: The dataset contains essential client information with over 400,000 observations.

- **Credit Data**: This dataset encompasses credit-related data of over one million observations. It contains key features such as MONTHS_BALANCE and STATUS.

The final sample for analysis contains over 36,000 unique applications that are common in both the datasets.

## Data Dictionary

| Column Name | Description | Data Type |
|-------------|-------------|----------|
| ID | Client identifcation number | int64 |
| is_delinquent | 1 is delinquent and 0 is paid off or no loan | bool |
| length_of_credit | Length of credit history in months | int64 |
| number_of_delinquent_months | Number of months with delinquency | int64 |
| average_delinquency_rate | Average delinquency rate | float64 |
| 3mo_delinquency | 1 is delinquent and 0 is paid off or no loan in the past 3 months | bool |
| FLAG_OWN_CAR | 1 indicates car ownership and 0 is no ownership | bool |
| FLAG_OWN_REALTY | 1 indicates property ownership and 0 is no ownership | bool |
| CNT_CHILDREN | Number of children | int64 |
| AMT_INCOME_TOTAL | Annual income | float64 |
| NAME_INCOME_TYPE | Category of income source | object |
| NAME_EDUCATION_TYPE | Education level | object |
| NAME_FAMILY_STATUS | Marital status | object |
| NAME_HOUSING_TYPE | Type of housing | object |
| FLAG_MOBIL | 1 indicates mobile phone ownership and 0 is no ownership | bool |
| FLAG_WORK_PHONE | 1 indicates work phone ownership and 0 is no ownership | bool |
| FLAG_PHONE | 1 indicates phone ownership and 0 is no ownership | bool |
| FLAG_EMAIL | 1 indicates email ownership and 0 is no ownership | bool |
| OCCUPATION_TYPE | Occupation | object |
| CNT_FAM_MEMBERS | Family size | int64 |
| AGE | Age | int64 |
| YEARS_EMPLOYED | Length of employment | int64 |

## Preliminary Data Analysis

The first stage involved conducting exploratory data analysis on the raw data. The primary aim was to assess data integrity and ensure consistency. This analysis revealed an unbalanced dataset with a significant proportion of individuals without any debt. The feature OCCUPATION_TYPE was the only column containing missing values. A segment of these were attributed to retirement, while the rest were simply missing. Additionally, it was observed that an anomaly existed in the MONTHS_BALANCE data with irregular jumps roughly every six months.

## Data Cleaning

The data cleaning process aimed at enhancing data quality by:

- Removing duplicated IDs: The dataset contained 47 duplicated IDs. It is crucial to note that no complete duplicates were identified in the samples, rather the ID's themselves were duplicated in error. A deeper analysis revealed substantial disparities among these, deeming it unreasonable to retain such instances. 

- Handling missing values: The missing values in the OCCUPATION_TYPE feature were addressed by creating a 'missing' label.

- Dropping irrelevant features: The GENDER feature was dropped to prevent systemic bias in the model predictions. Similarly, DAYS_EMPLOYED and DAYS_BIRTH features were dropped as they did not provide valuable human-readable information.

- Generating new features: In addition to the original features, new ones were created such as is_delinquent, length_of_credit, 6mo_delinquency, 12mo_delinquency, and more.

- Merging datasets: The application and credit datasets were merged along the 36,457 unique IDs shared between both datasets to create a comprehensive dataset for further analysis.

- A custom function, credit_approval_data_cleaner, was utilized to clean the training data. The test set data was cleaned in the model evaluation stage.

## Exploratory Data Analysis with Cleaned Data

The cleaned dataset was then subjected to further EDA to gain insights into the relationships among variables and potential correlations. Certain correlations such as between the count of children and family count were deemed unimportant. However, there were interesting negative correlations identified between the length of credit and delinquency. Graphical analysis revealed that having a car or property significantly influenced the length of credit rather than the number of delinquent months or the average delinquency rate.

## Project Contributors

This project has been a collaborative effort by our team members:

- Argishti Ovsepyan
- Masood Dastan
- Gabriella Fichtner
- Saamir Shamsie