# Data Science Salary Estimator: Project Overview

- Scraped over 1000 job descriptions from glassdoor using python and selenium
- Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark.
- Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model.

# Web Scraping

Tweaked the web scraper github repo  to scrape 1000 job postings from glassdoor.com. With each job, we got the following:

- Job title
- Salary Estimate
- Job Description
- Rating
- Company
- Location
- Company Headquarters
- Company Size
- Company Founded Date
- Type of Ownership
- Industry
- Sector
- Revenue
- Competitors

# Data Cleaning

After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

- Parsed numeric data out of salary
- Made columns for employer provided salary and hourly wages
- Removed rows without salary
- Parsed rating out of company text
- Made a new column for company state
- Added a column for if the job was at the company’s headquarters
- Transformed founded date into age of company
- Made columns for if different skills were listed in the job description:
  
    * Python
    * R
    * Excel
    * AWS
    * Spark
 
- Column for simplified job title and Seniority
- Column for description length

# EDA

I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables.

![Job_simp](https://github.com/anteportas2023/ds_salary_proj/blob/main/firefox_X7Y8zObi9Q.png)
![Location](https://github.com/anteportas2023/ds_salary_proj/blob/main/firefox_QgwQJnixf8.png)
![Heat map](https://github.com/anteportas2023/ds_salary_proj/blob/main/firefox_HX9kAdDAp5.png)

# Model Building

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:

- **Multiple Linear Regression** – Baseline for the model
- **Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
- **Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit.

# Model performance

The Random Forest model far outperformed the other approaches on the test and validation sets.

- Random Forest : MAE = -15.11
- Linear Regression: MAE = -20.77
- Ridge Regression: MAE = -19.26



