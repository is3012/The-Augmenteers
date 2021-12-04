# Data Analytics Project
# Suicide Rate Analysis Using Machine Learning Algorithm
Before executing the notebook in your device change the path to the directory where the dataset is present.
Dataset is been uploaded in the repository. We first imported some of the libraries that are useful for our project such as pandas, numpy, matplotlib, seaborn and many other.
We have used Suicides Rates Overview 1985-2014 dataset in our project.
We imported the dataset using read_csv() function.
While understanding the dataset, we observed that our dataset contained 12 attributes/columns and there are 27,820 rows.
This Dataset contains a combination of numerical and categorical features.</br>
# Categorical </br>
• Country</br>
• Year: 1986 to 2016</br>
• Sex: Male/female </br>
• Age: Five age groups</br> 
• Generation</br>
# Numerical</br>
• Population</br>
• Number of Suicides: Suicide incidences</br> 
• Suicides per 100k people: normalized version of suicide incidences</br>
• GDP for year: Gross Domestic Product (a measure of economic 
development)</br>
• GDP per capita for year: GDP/population</br>
• HDI for year: Human Development Index</br>
</br>
  We then checked the missing and duplicate values in our dataset. 'HDI for year' column has NaN values.</br>
  We have used another dataset to compute the NaN values. The dataset in provided in the repository.</br>
  # Explanatory Data Analysis
  1. We plotted a line graph using seaborn library, which shows the suicide incidence over the past 20 years.</br>
  The suicide incidence of the countries in our dataset peaked in 1995 and followed a downtrend since then. However, in 2015, there was a sudden surge of number of suicides.</br>
  2. We plotted a barplot using seaborn library, which visualizes the number of suicides by age and gender.</br>Older adults have a higher tendency of committing suicide. This might be related to factors such as loneliness, social connectedness, chronic diseases, etc.</br>
  3. We plotted a heatmap using the seaborn library, we visualized the correlation between numeric variables and suicide.</br>
# Prepare the Data for training
We'll follow the general steps below to prepare dataset for training.</br>
1. Create the target column</br>
2. Create a train/validation/test split</br>
3. Identify input and target columns</br>
4. Identify numeric and categorical columns</br>
5. Impute missing numeric values</br>
6. Scale numeric values</br>
7. Encode categorical columns</br>
# 1. Create the target column
Before we split the dataset into train/validation/test set, let's create our target column suicide_risk (i.e. high / low risk) using the information from suicides/100k pop.
If the value of suicides/100k pop is higher than the mean of suicides/100k pop, we will classify the suicide risk as high, and low otherwise.
# 2. Create Train, Validation and Test Sets
Let's split our dataset into three parts.

Train set: used to train a model
Validation set: used to tune model hyperparameters (e.g., regularization parameter) and choose between models during training
Test set: used to compare different models and report the model's final accuracy
In general, we can pick random subset of rows to create train/validation/test set in a distribution of 60-20-20 rule. However, when working with time-series data, it's better to split the dataset based on time, so the model was trained using the data in the past, and evaluated using the data in the future.
# 3. Identify Input and Target Columns
Often, not all the columns in the dataset are useful for training a model. We will ignore the following columns:

year: this is not relevant as we are predicting the suicide risk of a particular person in the future
suicides_no, population: contains redundant information as suicides/100k pop
suicides/100k pop: contains redundant information as suicide_risk
gdp_for_year ($): contains redundant information as gdp_per_capita ($)
generation: contains redundant information as age. Each generation is corresponding to a specific age group under age.
# 4. Identify numerical and categorical columns
We'll skip the step of missing value imputation as we have handled the missing values of HDI for year before performing exploratory data analysis. There is no null data in other columns.
