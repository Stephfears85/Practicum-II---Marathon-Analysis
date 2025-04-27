# Marathon Performance Analysis - Data Science Practicum

## Overview

This project comprises two Jupyter Notebooks designed to analyze marathon runner performance data. The project's overarching goal is to gain insights into factors influencing marathon success, runner behavior, and the impact of race course characteristics. The notebooks address the following key research questions:

1.  What are the key performance indicators that define marathon success?
2.  How do age, gender, and experience influence a runner's race?
3.  How does course difficulty, particularly elevation, impact finishing times across different races?
4.  What are the pacing strategies that lead to optimal results, and how do runners vary their pace throughout the race?

## Notebook 1: `practicum_ii_marathon.py`

### 1. Purpose/Goal

This notebook focuses on analyzing marathon runner performance data from multiple years to identify key performance indicators and explore the influence of runner demographics (age, gender) and experience on race outcomes. It also performs feature engineering to derive new metrics related to pacing and race strategy.

### 2. Key Sections/Steps

- Creating API’s to pull data from baa.org and athlinks.com for runner data
- goandrace.com and **** extracted GPX file for elevation data specific to each marathon
-   **Data Loading and Initial Exploration:** Loads marathon results data from CSV files for multiple years (2022, 2023, 2024) and performs initial data inspection (shape, data types, missing values).
-   **Data Cleaning and Imputation:** Cleans gender data, handles missing values in pace-related columns using linear interpolation and extrapolation, and verifies the imputation.
-   **Correlation Analysis:** Calculates and visualizes the correlation matrix to understand relationships between different performance metrics.
-   **Feature Engineering:** Creates new features such as split time ratios, halfway split percentage, pace variations, pace degradation, and negative split indicator.
-   **Runner Experience Calculation:** Identifies runners who have participated in multiple marathon years and calculates their marathon count.
-   **Age and Gender Grouping:** Creates age groups and combined age-gender groups for more granular analysis.
-   **Exploratory Data Analysis (EDA):** Visualizes the distribution of halfway split percentage, pace degradation, and other key variables using histograms and box plots.
-   **Machine Learning Process:**
    -   Filters data for runners who have run all three years.
    -   Calculates the best official time for these runners.
    -   Prepares data for machine learning by handling missing values, encoding categorical variables, scaling numerical features.
    -   Trains and evaluates a Linear Regression model (and potentially other models like Random Forest and Gradient Boosting) to predict pace.
    -   Performs residual analysis to assess model fit.
    -   Compares actual vs. predicted times and visualizes the results.

### 3. Key Libraries/Dependencies

-   `pandas`: Data manipulation and analysis.
-   `plotly.express`: Interactive plotting.
-   `plotly.graph_objects`: Advanced plotting.
-   `numpy`: Numerical operations.
-   `matplotlib.pyplot`: Basic plotting.
-   `seaborn`: Statistical data visualization.
-   `re`: Regular expressions for text processing.
-   `sklearn.model_selection`: Model selection and data splitting.
-   `sklearn.linear_model`: Linear Regression model.
-   `sklearn.ensemble`: Random Forest and Gradient Boosting Regressors.
-   `sklearn.metrics`: Model evaluation metrics.
-   `sklearn.preprocessing`: Data scaling and encoding.
-   `sklearn.impute`: Missing value imputation.

### 4. Input Data

-   **Data Source:** `marathon_results_2022.csv`, `marathon_results_2023.csv`, `marathon_results_2024.csv`
-   **Format:** CSV (Comma-Separated Values)
-   **Location:** The data files are assumed to be in the same directory as the notebook.
-   **Description:** These CSV files contain marathon runner results data, including race times at various checkpoints, age, gender, and other runner information.

### 5. Output

-   **Visualizations:** Histograms, box plots, scatter plots, and other visualizations exploring runner performance, pace variations, and the influence of age and gender.
-   **Machine Learning Model Evaluation Metrics:** Mean Squared Error (MSE) and R-squared (R²) for the pace prediction models.
-   **Residual Analysis Plots:** Plots to assess the fit and potential issues with the regression models.
-   **DataFrames with Engineered Features:** The notebook generates DataFrames with new columns representing pace ratios, pace degradation, and other calculated metrics.

### 6. Assumptions/Prerequisites

-   The input CSV files (`marathon_results_2022.csv`, `marathon_results_2023.csv`, `marathon_results_2024.csv`) must be present in the same directory as the notebook.
-   The required Python libraries listed in "Key Libraries/Dependencies" must be installed.

### 7. Usage Instructions

1.  Ensure all required libraries are installed (`pip install pandas plotly numpy matplotlib seaborn scikit-learn`).
2.  Place the input CSV files in the same directory as the notebook.
3.  Run the notebook cells sequentially to execute the data analysis and modeling pipeline.
4.  Adjust any file paths or parameters as needed within the notebook.

### 8. Potential Issues/Limitations

-   The imputation method for missing values is a simplified linear interpolation/extrapolation. More sophisticated imputation techniques could be explored.
-   The analysis focuses primarily on readily available data. Additional factors like weather conditions, runner training, and course-specific details could provide further insights.
-   The machine learning models are trained on a subset of runners (those who ran all three years) and may not generalize perfectly to all runners.

## Notebook 2: `boston_steamboat_copy4_24_(2) (1).py`

### 1. Purpose/Goal

This notebook focuses on comparing runner performance and pace between the Boston Marathon and the Steamboat Marathon. It aims to analyze the impact of course differences (particularly elevation) on runner times and pacing strategies.

### 2. Key Sections/Steps

-   **Data Loading:** Loads race results data for the Steamboat and Boston Marathons from CSV files.
-   **Data Cleaning and Transformation:**
    -   Converts time strings to timedelta objects for analysis.
    -   Cleans gender data.
    -   Handles missing data.
-   **Descriptive Statistics:** Calculates and prints descriptive statistics for overall times for both races, broken down by gender.
-   **Time Distribution Visualization:** Creates histograms and box plots to visualize the distribution of finishing times for male and female runners in both marathons.
-   **Elevation Data Loading and Visualization:**
    -   Loads elevation data from GPX files for both marathons.
    -   Visualizes the elevation profiles of the courses.
-   **Half and Full Marathon Comparisons:**
    -   Compares half and full marathon times between Steamboat and Boston, broken down by gender.
    -   Uses box plots to visualize these comparisons.
-   **Statistical Tests (Optional):** Performs t-tests to statistically compare the mean finishing times between the two races.

### 3. Key Libraries/Dependencies

-   `pandas`: Data manipulation and analysis.
-   `numpy`: Numerical operations.
-   `matplotlib.pyplot`: Basic plotting.
-   `seaborn`: Statistical data visualization.
-   `gpxpy`: GPX file parsing for elevation data.
-   `scipy.stats`: Statistical tests.
-   `matplotlib.dates`: Handling date/time objects for plotting.

### 4. Input Data

-   **Marathon Results Data Source:** `steamboat_race_results.csv`, `marathon_results_2024.csv`
-   **Format:** CSV
-   **Location:** The data files are assumed to be in the `C:\Users\Steph\OneDrive\Desktop\` directory.
-   **Description:** These CSV files contain race results for the Steamboat and Boston Marathons, including runner times and demographic information.
-   **Elevation Data Source:** `Steamboat Springs Marathon.gpx`, `gpx_20240415_id8675_race1_20240125224011.gpx`
-   **Format:** GPX (GPS Exchange Format)
-   **Location:** The GPX files are assumed to be in the `C:\Users\steph\Downloads\` directory.
-   **Description:** These GPX files contain geographical data, including elevation information, for the marathon courses.

### 5. Output

-   **Descriptive Statistics:** Tables summarizing key statistics (mean, standard deviation, etc.) for finishing times.
-   **Visualizations:** Histograms, box plots, and elevation profiles comparing runner performance and course difficulty.
-   **Statistical Test Results:** P-values and t-statistics from the comparison of finishing times.
-   **DataFrames for Comparison:** DataFrames specifically created to compare Steamboat and Boston marathon times.

### 6. Assumptions/Prerequisites

-   The input CSV files can be found in the github repository directory.
-   The input GPX files must be present in the can be found in the github repository directory.
-   The required Python libraries listed in "Key Libraries/Dependencies" must be installed (`pip install pandas numpy matplotlib seaborn gpxpy scipy`).

### 7. Usage Instructions

1.  Ensure all required libraries are installed (`pip install pandas numpy matplotlib seaborn gpxpy scipy`).
2.  Place the input CSV and GPX files in the specified directories.
3.  Run the notebook cells sequentially to execute the data analysis and visualization pipeline.
4.  **Important:** The file paths in this notebook are hardcoded. You will need to modify the `file_path` variables to point to the correct locations of your data files.

### 8. Potential Issues/Limitations

-   The notebook's file paths are hardcoded, making it less portable.
-   The elevation analysis relies on the accuracy and completeness of the GPX files.
-   The statistical tests are basic t-tests. More advanced statistical methods could be used to account for other factors.



