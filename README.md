# PySpark_Project
# LendingClub Loan Defaulters Analysis (PySpark)

This project aims to analyze the LendingClub dataset to identify patterns in borrower behavior and determine factors contributing to loan default. The project involves large-scale data cleaning, feature engineering, data segmentation, and preparation for modeling using **PySpark**.


## Objective

To process and clean a large LendingClub loan dataset, derive meaningful insights, classify borrowers based on risk, and prepare the data for future modeling (classification/prediction of defaulters).


## Tools & Technologies

- **PySpark (Spark DataFrame API)**
- **Jupyter Notebook**

## Project Structure

The dataset was too large to process in one go, so we modularized it into stages:

### Notebooks Breakdown:

- `LendingClub_Intro.ipynb`:  
  Dataset overview, initial schema inspection, basic profiling.

- `LendingClub_DataCleaning_S1.ipynb`:  
  First stage of data cleanup — removed irrelevant fields, handled nulls, type conversions.

- `LendingClub_DataCleaning_S2.ipynb`:  
  Cleaned remaining columns, dropped duplicates, normalized categorical fields.

- `LendingClub_DataCleaning_S3.ipynb`:  
  Identified loan status categories and segregated default vs non-default records.

- `LendingClub_DataCleaning_S4.ipynb`:  
  Cleaned and saved the data to various files for processing further.

- `LendingClub_S5_S6.ipynb`,`LendingClub_S7.ipynb`:  
  Final cleaning, null handling, Feature creation – calculated loan scores based on risk features like loan purpose, int_rate, and emp_length.

## Key Transformations & Insights

- Removed unwanted fields like `url`, `desc`, `member_id`, etc.
- Converted percentage strings (like `int_rate`) to float for calculations.
- Cleaned and standardized fields such as `emp_length`, `issue_d`, and others.
- Created a binary target column:  
  `default_flag = 1` if loan was "Charged Off" or "Default", else 0.
- Encoded `member_id` using SHA-2 hashing to generate `encoded_borrower_id`.
- Used a configurable scoring system based on business rules to assign a `loan_score`:
  - Score buckets defined for `purpose`, `emp_length`, and `annual_inc`
- Segregated data into high-risk and low-risk categories using `loan_score` and `default_flag`.
- Cleaned and transformed data saved as partitioned Parquet files for downstream ML use.

  
## Outcome

- **Cleaned & enriched dataset** ready for modeling.
- **Feature-engineered loan scores** based on multi-attribute logic.
- Modular notebook structure allows easy future extension (ML modeling, reporting).

## Dataset Source

Data sourced from [LendingClub's Public Loan Data Repository](https://www.lendingclub.com/info/download-data.action)

## Author

**Sugirtha C**  
Learning Path: Functional QA → Big Data Transition  
Technologies: PySpark, Azure ADF, Databricks, SQL, Test Automation Frameworks-Selenium/RestAPI

## Disclaimer

This is a **self-learning project** and not affiliated with LendingClub. Data cleaning and transformation logic is customized for education and practice purposes.
