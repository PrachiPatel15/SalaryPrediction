![](https://github.com/PrachiPatel15/SalaryPrediction/blob/main/wordcloud.png)

# Data Science Salary Estimator: Project Overview
- Created a project that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
- Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark.
- Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model.
- Built a client facing API using flask

# Code and Resources Used
- ***Python Version:*** 3.7
- ***Packages:*** pandas, numpy, sklearn, matplotlib, seaborn, selenium, flask, json, pickle
- ***For Web Framework Requirements:*** ```pip install -r requirements.txt```
- ***Dataset:*** (https://github.com/PrachiPatel15/SalaryPrediction/blob/main/glassdoor_jobs.csv)

# Data
- In the data, with each job, we got the following attributes:
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
After getting the data, I needed to clean it up so that it can be used for our model. I made the following changes:
- Parsed numeric data out of salary
- Made columns for employer provided salary and hourly wages
- Removed rows without salary
- Parsed rating out of company text
- Made a new column for company state
- Added a column for if the job was at the company’s headquarters
- Transformed founded date into age of company
- Made columns for if different skills were listed in the job description:
  - Python
  - R
  - Excel
  - AWS
  - Spark
- Column for simplified job title and Seniority
- Column for description length

# EDA
When I was visualizing the data and the value counts for the various categorical variables found some correlation and built some table tables for building a better model. Here are some of the pictures.
![](https://github.com/PrachiPatel15/SalaryPrediction/blob/main/salary_by_job_title.png)![](https://github.com/PrachiPatel15/SalaryPrediction/blob/main/location_wise_jobs.png) ![](https://github.com/PrachiPatel15/SalaryPrediction/blob/main/correlation_visual.png)

# Model Building
First, i needed to create dummy variables as the data contains lots of catagorical attributes. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:
- Multiple Linear Regression – Baseline for the model
- Lasso Regression 
- Random Forest 

# Model performance
The Random Forest model performed the **best** to the other approaches on the test and validation sets.
- Random Forest : MAE = 10.89
- Linear Regression: MAE = 18.56
- Lasso Regression: MAE = 19.65

# Productionization
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary.
