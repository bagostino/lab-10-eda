# Lab — Exploratory Data Analysis with Ames Housing

## Overview

In this lab, you will practice exploratory data analysis (EDA) using the Ames Housing dataset.

The goal is not to follow a rigid checklist. The goal is to investigate the dataset, ask useful questions, and use summary statistics, grouping, missing-value checks, and light visualization to understand what the data is telling you.

## Guiding Question

> **What factors appear to influence home sale price?**

You will use this question to guide your analysis. As you work, keep asking:

- What variables seem important?
- What patterns do I notice?
- What surprises me?
- What should I investigate next?

## Dataset

This lab uses the Ames Housing dataset, originally compiled by Dean De Cock for data science education.

Recommended download source:

- [Ames Housing CSV from Rdatasets](https://vincentarelbundock.github.io/Rdatasets/csv/modeldata/ames.csv)

Suggested repo structure:

```text
project-folder/
├── data/
│   └── ames.csv
├── starter-code.ipynb
└── README.md
```

## Learning Objectives

By the end of this lab, you will be able to:

- Load and inspect a real-world dataset with Pandas
- Identify numeric and categorical variables
- Detect and reason about missing values
- Calculate and interpret summary statistics
- Use `.value_counts()` and `.value_counts(normalize=True)` for categorical variables
- Use `.groupby()` to compare numeric variables across categories
- Use covariance and correlation to investigate numeric relationships
- Create simple Pandas plots to support your analysis
- Write short interpretations of your findings

## Key EDA Mindset

EDA is not:

- Running `.describe()` and stopping
- Making random plots
- Following the same steps for every dataset

EDA is:

> **Asking questions, investigating patterns, and explaining what the data suggests.**

You are not expected to find one perfect answer. You are expected to support your thinking with evidence.

---

## Part 1 — Load and Inspect the Data

### Tasks

1. Import Pandas.
2. Load `data/ames.csv` into a DataFrame.
3. Display the first few rows.
4. Check the shape of the dataset.
5. Review the column names.
6. Check the data types.

### Reflection Questions

- How many rows and columns are in the dataset?
- Which column appears to be the target variable?
- Which variables appear numeric?
- Which variables appear categorical?

---

## Part 2 — Focus the Dataset

The full Ames dataset has many columns. For this lab, focus on a smaller set of variables so you can practice EDA without getting overwhelmed.

Use the following columns if they are available in your version of the dataset:

```python
columns_to_use = [
    'Sale_Price',
    'Gr_Liv_Area',
    'Overall_Qual',
    'Year_Built',
    'Lot_Area',
    'Lot_Frontage',
    'Neighborhood',
    'House_Style',
    'Garage_Type',
    'Central_Air'
]
```

If your column names are different, adjust them as needed.

### Tasks

1. Create a smaller DataFrame using the columns above.
2. Inspect the first few rows.
3. Check the data types again.

### Reflection Questions

- Why might it be useful to focus on fewer variables during EDA?
- Which selected variables are numeric?
- Which selected variables are categorical?

---

## Part 3 — Missing Values

Before analyzing relationships, you need to understand where data is missing.

### Tasks

1. Count missing values in each column.
2. Calculate the percentage of missing values in each column.
3. Decide how to handle missing values for this lab.

### Suggested Imputation Strategy

Use simple imputation only:

- For numeric columns: fill missing values with the median
- For categorical columns: fill missing values with `'Missing'`

This is not always the best strategy in production, but it is good enough for this EDA lab.

### Reflection Questions

- Which columns have missing values?
- Why might the median be safer than the mean for numeric imputation?
- Why might we use `'Missing'` instead of dropping categorical rows?

---

## Part 4 — Summary Statistics for Numeric Variables

Now explore the numeric variables individually.

### Tasks

1. Use `.describe()` on the numeric columns.
2. Manually calculate the mean of `Sale_Price`.
3. Manually calculate the median of `Sale_Price`.
4. Calculate the standard deviation of `Sale_Price`.
5. Compare your manual calculations to Pandas methods.

### Helpful Formulas

Mean:

$$
\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_i
$$

Sample standard deviation:

$$
s = \sqrt{\frac{1}{n - 1} \sum_{i=1}^{n} (x_i - \bar{x})^2}
$$

### Reflection Questions

- What is the average sale price?
- Is the mean higher or lower than the median?
- What might that tell you about the distribution of sale prices?
- Is there a wide range of home prices?

---

## Part 5 — Categorical Variables

Categorical variables describe groups or labels.

For categorical variables, we usually ask:

> **What categories exist, and how common is each category?**

### Tasks

1. Use `.value_counts()` on `Neighborhood`.
2. Use `.value_counts(normalize=True)` on `Neighborhood`.
3. Repeat the process for `House_Style`, `Garage_Type`, and `Central_Air`.
4. Create a bar plot for one categorical variable using Pandas plotting.

### Reflection Questions

- Which neighborhood appears most often?
- Are some categories rare?
- Why are proportions sometimes more helpful than raw counts?

---

## Part 6 — Grouped Summary Statistics

Now use `.groupby()` to compare sale prices across categories.

### Tasks

1. Calculate average sale price by `Neighborhood`.
2. Calculate median sale price by `Neighborhood`.
3. Calculate average sale price by `House_Style`.
4. Calculate average sale price by `Central_Air`.
5. Sort your results from highest to lowest.

### Reflection Questions

- Which neighborhoods have the highest average sale price?
- Do mean and median tell the same story?
- Does central air appear related to sale price?
- What other variables would you group by?

---

## Part 7 — Covariance and Correlation

Grouped summaries help compare categories. Correlation helps compare numeric variables.

Covariance tells us whether two variables move together, but it is hard to interpret because it depends on units.

Correlation standardizes that relationship between -1 and 1.

### Tasks

1. Create a correlation matrix for the numeric variables.
2. Identify which numeric variables have the strongest correlation with `Sale_Price`.
3. Calculate the covariance between `Gr_Liv_Area` and `Sale_Price`.
4. Calculate the correlation between `Gr_Liv_Area` and `Sale_Price`.

### Helpful Formula

Correlation:

$$
r = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \bar{x})^2} \sqrt{\sum_{i=1}^{n} (y_i - \bar{y})^2}}
$$

### Reflection Questions

- Which numeric variable appears most related to sale price?
- Is the relationship positive or negative?
- Why is correlation easier to interpret than covariance?
- What does correlation not prove?

---

## Part 8 — Pandas Plots

Use visualization to support your analysis.

### Required Plots

Create at least three plots using Pandas plotting methods:

1. Histogram of `Sale_Price`
2. Scatter plot of `Gr_Liv_Area` vs `Sale_Price`
3. Bar plot of average `Sale_Price` by one categorical variable

### Reflection Questions

- What does the sale price distribution look like?
- Does living area appear related to sale price?
- Which categorical comparison was most useful?

---

## Part 9 — Final Written Analysis

Write a short summary of your findings.

Your response should answer:

1. What factors appear most related to sale price?
2. What evidence supports your answer?
3. What surprised you?
4. What would you investigate next?
5. What limitations should we keep in mind?

### Minimum Requirements

Your final analysis should include:

- At least two numeric findings
- At least one categorical comparison
- At least one plot-based observation
- At least one limitation or caution

---

## Submission Checklist

Before submitting, make sure you have:

- Loaded the dataset successfully
- Checked missing values
- Applied simple imputation
- Used summary statistics
- Used `.value_counts()`
- Used `.groupby()`
- Used covariance or correlation
- Created at least three Pandas plots
- Written a final interpretation

---

## Important Reminder

> Correlation does not imply causation.

EDA helps us find patterns. It does not prove cause and effect.
