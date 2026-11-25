# EDA Project: Exploratory Analysis of House Prices

## Project Overview

This project performs **Exploratory Data Analysis (EDA)** on the Ames Housing Dataset from Kaggle's *House Prices: Advanced Regression Techniques* competition.

- **Dataset file:** `train.csv`
- **Approximate size:** 1,460 rows and 81 columns
- **Goal:** Understand which factors are associated with house sale prices using EDA only.
- **Machine learning:** Not included in this project.

## Objectives

The analysis investigates these questions:

1. How is `SalePrice` distributed? Is it skewed?
2. Which numerical features have the strongest correlation with `SalePrice`?
3. Does `OverallQual` show an ordered relationship with sale price?
4. Do some neighborhoods have consistently higher house prices?
5. Are there outliers, and do they represent errors or unusual but valid sales?
6. Which columns contain missing values, and do some missing values indicate that a feature is absent?

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook

Install the packages listed in `requirement.text` before running the notebook.

## Project Workflow

The notebook follows this suggested structure:

1. **Introduction** — objective, dataset description, and guiding questions.
2. **Data loading** — load `train.csv`, inspect its shape, data types, and missing values.
3. **Data understanding** — classify variables and calculate descriptive statistics.
4. **Data cleaning** — check duplicates, inconsistent categories, missing values, and impossible values.
5. **Univariate analysis** — study distributions using histograms, KDE plots, and boxplots.
6. **Bivariate and multivariate analysis** — explore correlations, scatter plots, and pair plots.
7. **Outlier analysis** — detect and compare outliers using IQR and z-score methods.
8. **Dashboard** — combine important visualizations into one figure.
9. **Conclusions** — summarize findings and limitations.

## Main Analysis Tasks

### 1. Setup and first look
- Import the required libraries.
- Read `train.csv` into a Pandas DataFrame.
- Inspect the dataset shape, first five rows, data types, and null counts.
- Report the columns with missing values and their percentages.

### 2. Classify variables
- Separate numerical and categorical columns.
- Identify ordinal variables such as `OverallQual`, `ExterQual`, and `KitchenQual`.
- Document each column's type, unique-value count, and example values.

### 3. Descriptive statistics
For `SalePrice`, `GrLivArea`, and `LotArea`, calculate:
- Mean, median, and mode
- Standard deviation and variance
- Range and interquartile range (IQR)
- Skewness and kurtosis

Also inspect value counts for `Neighborhood` and `HouseStyle`.

### 4. Distributions
- Plot the `SalePrice` histogram with a KDE overlay.
- Create a `SalePrice` boxplot.
- Compare the original and log-transformed `SalePrice` distributions.
- Plot sale prices by `OverallQual` and `Neighborhood`.
- Create count plots for `OverallQual` and `HouseStyle`.

### 5. Correlation and covariance
- Calculate covariance and Pearson correlation matrices for numerical columns.
- List the ten features most correlated with `SalePrice`.
- Explain why correlation is easier to compare across features than covariance.
- Optionally calculate Spearman correlation for ordinal variables.
- Remember: correlation does not imply causation.

### 6. Scatter plots and pair plots
- Plot `GrLivArea` against `SalePrice`.
- Plot `TotalBsmtSF` against `SalePrice`.
- Plot `YearBuilt` against `SalePrice`.
- Create a pair plot for `SalePrice`, `GrLivArea`, `TotalBsmtSF`, `GarageArea`, and `YearBuilt`.
- Inspect unusually large houses with comparatively low sale prices.

### 7. Correlation heatmap
- Select the ten features most correlated with `SalePrice`.
- Create an annotated correlation heatmap.
- Use a diverging colour map centered at zero and mask the duplicate upper triangle.

### 8. Outlier detection
- Implement the IQR method using the 1.5 × IQR rule.
- Implement the z-score method using an absolute z-score threshold of 3.
- Compare outlier counts and overlap for `GrLivArea` and `SalePrice`.
- Inspect flagged points before deciding whether to remove or retain them.

### 9. Data quality checks
- Count and remove duplicate rows if present.
- Check categorical values for casing, extra spaces, and spelling inconsistencies.
- For the dataset columns `PoolQC`, `Alley`, `Fence`, `FireplaceQu`, and `GarageType`, consider whether a null means the feature is absent; document the decision.
- Handle numerical missing values, for example `LotFrontage`, using an appropriate median strategy.
- Check for impossible values such as `YearBuilt > YrSold` or negative area values.
- Verify remaining missing values after cleaning.

### 10. Final dashboard
Create a 2 × 2 dashboard containing:
1. A line plot of average `SalePrice` by `YearBuilt`.
2. A horizontal bar plot of the ten neighborhoods with the highest mean sale price.
3. A `SalePrice` histogram with KDE and mean/median reference lines.
4. A scatter plot of `GrLivArea` versus `SalePrice`, coloured by `OverallQual`.

Save the figure as `eda_dashboard.png`.

## Expected Insights to Verify

These are hypotheses to investigate, not results to assume:

- `SalePrice` may be right-skewed, and a log transformation may make its distribution closer to normal.
- `OverallQual` and `GrLivArea` may be among the features most strongly correlated with price.
- Sale price may rise with overall quality, with greater spread at higher quality levels.
- Some neighborhoods may have higher median prices than others.
- A small number of very large houses with low prices may influence trend patterns.
- Many apparent missing values may actually mean that a feature is absent.

## Running the Project

1. Download the Ames Housing `train.csv` dataset from Kaggle's *House Prices: Advanced Regression Techniques* competition.
2. Place `train.csv` in the project directory (or update the notebook's file path).
3. Install the dependencies:

   ```bash
   pip install -r requirement.text
   ```

4. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Run the notebook cells in order and record interpretations in Markdown cells.

## Notebook Documentation

Add a Markdown cell before each code cell explaining what will be done, and a Markdown cell after it explaining what was learned.

## Scope and Limitations

This is an exploratory analysis project. It does not train or evaluate a machine-learning model, and it should not claim that correlations prove causal relationships. Outliers and missing values should be interpreted using the dataset context and documented decisions.
