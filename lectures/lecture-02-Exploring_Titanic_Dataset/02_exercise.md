## 📝 EDA Practice Exercise – Tips Dataset

## Objective

## Perform the first six steps of Exploratory Data Analysis (EDA) using the Tips dataset.

### step 1: Import Libraries

Import the following libraries:

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

### step 2: Load the Dataset
df = sns.load_dataset("tips")

### step 3: Inspect the Dataset
Write code to answer the following:
Display the first 8 rows.
Display the last 5 rows.
Find the shape of the dataset.
Display all column names.
Show the data type of each column.
Display summary statistics.

### step 4: Missing Values

Write code to:

Check whether the dataset contains missing values.
Count missing values in each column.
Calculate the percentage of missing values.
Which column has the highest number of missing values?

### step 5: Explore Columns
Write code to:

Display only the total_bill column.
Display total_bill and tip together.
Display sex, smoker, and day together.