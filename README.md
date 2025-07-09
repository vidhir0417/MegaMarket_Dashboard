# README: Mega Market - Data Pre-Processing and Visualization

This document details the strategic initiative undertaken by a group of data scientists to transform raw transactional data into a format suitable for advanced analysis and valuable business insights.

## Purpose

The primary objective of this project was to:

* Transform raw transactional data into a clean, consistent and analyzable format.

* Address data quality issues such as missing values, outliers and inconsistencies.

* Create an Analytical Base Table (ABT) to support business problem-solving and machine learning models.

* Segment customers based on their loyalty and spending patterns.

* Provide interactive and easy-to-understand visualizations of key business insights.

## Project Phases & Methodology

The project followed a multi-stage approach, leveraging various tools:

### 1. Data Analysis & Initial Exploration (SAS Enterprise Miner)

* Analyzed raw data, including descriptive statistics of interval and categorical variables.

* Identified missing values (Age, Monthly Income, Kids, Reviews) and potential outliers (Monthly Income, Quantity, Age).

* Examined correlations between variables (e.g., Total Paid, Unit Price, Quantity).

* Visualized variable distributions.

### 2. Outlier and Missing Value Treatment (SAS Enterprise Miner)

* **Outlier Treatment:** Deleted outliers (e.g., Age > 100, extreme Monthly Income/Quantity values), ensuring less than 3% data removal.

* **Missing Value Imputation:** Imputed missing values for Age, Monthly Income and Kids using a decision tree model. The 'Reviews' variable was dropped due to a high percentage of missing values.

* **Variable Transformations:** Applied transformations (e.g., optimal binning for Unit Price, Log transformation for Total Paid) to achieve more normal distributions for certain variables.

### 3. Coherence Checking (Python & SAS Studio)

* **Python (Jupyter Notebooks):**

  * Identified and removed customer-related inconsistencies (e.g., same customer with different genders or nationalities across transactions).

  * Checked for logical inconsistencies (e.g., online transactions paid with cash).

* **SAS Studio (SQL):**

  * Checked sales-related inconsistencies (e.g., negative Unit Price, Total Paid, or Quantity).

  * Ensured `Total Paid` was consistent with `Unit Price * Quantity`.

  * In total, 434 inconsistent observations were deleted to increase data credibility.

### 4. Analytical Base Table (ABT) Creation (SAS Studio & Python)

* Created new variables in SAS Studio using SQL, including:

  * `Frequency` (transaction count per product category per customer)

  * `Monetary` (total money spent per product category per customer)

  * `First Purchase` and `Last Purchase` dates per customer

  * `Lowest Purchase`, `Highest Purchase`, `Average Purchase` per product category per customer

  * `Percentage` of transactions in each product category per customer

  * Binary flags for `Payment Type` and `Store Type` usage.

* Merged all new variables into a final ABT, handling `None` values by converting them to 0.

* Rounded imputed numerical variables (e.g., Age, Monthly Income) in Python.

### 5. Customer Segmentation (Python)

* Segmented customers into **Bronze**, **Silver** and **Gold** categories based on their `Total Spent` using percentiles (33rd and 66th).

### 6. Visualization (PowerBI)

* Created interactive dashboards in PowerBI for:

  * **Customer Analysis:** Insights on customer demographics, payment types, store preferences and first purchase trends.

  * **Sales Analysis:** Trends in monthly income vs. total spent, transactions per day and total sales per product category.

  * **Product Analysis:** Quantity per unit price, quantity per product category, monthly income per quantity and quantity per payment type.

* Implemented interactive buttons for filtering by gender, time period, product category and store type.

## Conclusion

The project successfully provided Mega Market with a deeper understanding of its customers, sales trends and product performance. The clean dataset and the Analytical Base Table serve as valuable assets for future projects, improving results and refining decision-making processes.
