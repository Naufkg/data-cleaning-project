# Data Cleaning Documentation
## Introduction
A dataset named messy_Data.csv

## Data Overview
The dataset consist of 11000 rows and 8 columns .Unnamed , ID , Name , Age , EMail ,Join Date , Salary and Department are the columns.
Here , This 'Unnamed' column is often created when a DataFrame with an index is saved to a CSV file and then reloaded.

## Initial Data Issues
1. **Missing Values**: Handled missing values in columns such as `Name`, `Age`, `Email`, `Join Date`, `Salary`, and `Department`.
2. **Invalid Entries**: Corrected invalid email formats and erroneous department names.
3. **Outliers**: Addressed outliers in numerical columns like `Age` and `Salary`.

## Cleaning Steps
1. **Remove Unnecessary Columns**:
   - Removed the unnamed index column.

2. **Handle Missing Values**:
   - Filled missing names with "Unknown Name".
   - Converted `Age` to numeric and filled missing values with the median.
   - Filled missing emails with "unknown@example.com".
   - Filled missing `Join Date` with the current date.
   - Filled missing `Department` with the mode.
   - Filled missing `Salary` with the median.
  
3. **Correcting Data Types**:
    - Converted Age column to numeric type.

4. **Correct Invalid Entries**:
   - Corrected email formats using regex.
   - Standardized department names using a predefined mapping.

 ## Outlier Detection and Handling
- **Age and Salary**: Used boxplots, IQR, and Z-score methods to detect outliers.
  - No significant outliers were found in Age and Salary.

5.**Salary Data Cleaning**:
   - Set boundaries based on statistical analysis:
     - Lower Bound: Q1 - 1.5 * IQR
     - Upper Bound: Q3 + 1.5 * IQR
   - Applied capping to ensure salaries fall within these boundaries.
   - Validated results by counting values outside the boundaries.

### Validation of Salary Data Cleaning
6. **Summary Statistics**:
   - Reviewed summary statistics to ensure all salary values fall within the defined boundaries.
   - And visualizations to confirm the cleaned data distribution.
   print(df['Salary'].describe())

## Final Validation Results
- Number of salaries below -9433.483545349256: 0
- Number of salaries above 189073.26636871079: 0

## Saving the Cleaned Dataset
Saved the cleaned dataset as `cleaned_dataset.csv`.
