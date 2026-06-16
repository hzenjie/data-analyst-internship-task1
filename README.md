# Data Analyst Internship - Task 1: Data Cleaning and Preprocessing

## Project Overview
This project fulfills Task 1 of the Data Analyst Internship, focusing on data cleaning and preprocessing raw data before it moves to the analysis or modeling phase.

## Dataset Used
* **Dataset Name:** Mall Customer Segmentation Data (`Mall_Customers.csv`)
* **Data Size:** 200 rows, 5 columns.

## Summary of Changes
1. **Column Name Standardization:** Converted the original column names (which contained spaces and special characters) into *snake_case* and *lowercase* formats for easier references in coding:
   * `CustomerID` -> `customerid`
   * `Gender` -> `gender`
   * `Age` -> `age`
   * `Annual Income (k$)` -> `annual_income_k`
   * `Spending Score (1-100)` -> `spending_score_1_100`
2. **Missing Values & Duplicates:** Verified the dataset using `.isnull()` and `.duplicated()`. The dataset contains no missing values or duplicate records, preserving the integrity of the original data.
3. **Text Standardization:** Applied string trimming (stripping whitespaces) on the `gender` column and ensured a uniform text format (*Title Case*).

## Repository Files
* `Mall_Customers.csv`: The original raw dataset.
* `mallcust.ipynb`: The Jupyter Notebook containing the data cleaning steps using Python Pandas.
* `cleaned_dataset.csv`: The final, cleaned dataset export.
* `README.md`: Project documentation and interview answers.

---

## Interview Questions & Answers (Task 1 Evaluation)

### 1. What are missing values and how do you handle them?
Missing values represent data points that are lost, unrecorded, or absent in a dataset (commonly appearing as `NaN` or `Null`). They can be handled using two main approaches:
* **Deletion:** Dropping the affected rows or columns using `.dropna()`, which is ideal if the missing data is negligible.
* **Imputation:** Filling in the missing blanks using `.fillna()` with statistical metrics such as Mean/Median (for numerical data) or Mode/new categories like 'Unknown' (for categorical data).

### 2. How do you treat duplicate records?
Duplicate records are managed by first detecting them using `.duplicated().sum()`. If duplicates are found, they should be removed using `.drop_duplicates(keep='first')` to prevent data redundancy from skewing statistical calculations and biasing analysis results.

### 3. Difference between dropna() and fillna() in Pandas?
* `dropna()` is used to **remove/drop** entire rows or columns that contain missing values.
* `fillna()` is used to **replace/fill** missing values with a specified alternative value (e.g., zero, mean, or a placeholder string) without deleting the row itself.

### 4. What is outlier treatment and why is it important?
Outlier treatment is the process of identifying and handling extreme data points that deviate significantly from the rest of the dataset. It is crucial because outliers can distort statistical summaries (such as inflating the *mean*), misrepresent data visualizations, and severely degrade the accuracy of machine learning models.

### 5. Explain the process of standardizing data.
Data standardization is the process of unifying formats, scales, or text representations to ensure consistency across the entire dataset. Examples include normalizing text cases (e.g., converting "MALE" and "male" uniformly into "Male"), formatting inconsistent date styles, or renaming column titles to a standard lowercase layout without spaces so code execution runs smoothly.

### 6. How do you handle inconsistent data formats (e.g., date/time)?
Inconsistent formats are resolved using built-in type conversion functions. In Pandas, this is typically done using `pd.to_datetime()` paired with the `errors='coerce'` parameter. This technique forces mismatched text-based dates into a uniform, standardized date format (YYYY-MM-DD).

### 7. What are common data cleaning challenges?
Key challenges include dealing with massive volumes of corrupted data, lack of proper data dictionaries (not knowing what a column or code means), human entry errors (typos, misspellings, or misplaced fields), and identifying hidden outliers that require domain knowledge to properly evaluate.

### 8. How can you check data quality?
Data quality is evaluated through Exploratory Data Analysis (EDA) methods, such as inspecting the structural summary of columns via `df.info()`, reviewing descriptive statistics using `df.describe()`, checking for total missing cells with `df.isnull().sum()`, and identifying unique textual categories using `df['column'].unique()`.
