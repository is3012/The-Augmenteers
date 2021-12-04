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
Before we split the dataset into train/validation/test set, let's create our target column suicide_rate (i.e. high / low risk) using the information from suicides/100k pop.
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
suicides/100k pop: contains redundant information as suicide_rate
gdp_for_year ($): contains redundant information as gdp_per_capita ($)
generation: contains redundant information as age. Each generation is corresponding to a specific age group under age.
# 4. Identify numerical and categorical columns
# 5. Impute missing numeric values
We'll skip the step of missing value imputation as we have handled the missing values of HDI for year before performing exploratory data analysis. There is no null data in other columns.
# 6. Scale Numeric Features
Let's scale the numeric features (i.e., HDI for year, gdp_per_capita) to a range of value of 0 to 1. This ensures that no particular numeric features has a disproportionate impact on the model's loss. It also smoothens the training process.

Let's use MinMaxScaler from sklearn.preprocessing to scale values to (0,1) range.
# 7. Encode categorical columns
To train the machine learning models, we need to transform the values of categorical columns into numbers. There are different ways to encode the data, such as label encoding and one-hot encoding.

Here, we will use OneHotEncoder from sklearn.preprocessing. What it does is to convert each category value into a new column and assign a 1 or 0 (True/False) value to the column. This has the benefit of not weighting a value improperly.

# Decision Tree
A decision tree is a flowchart-like structure in which each internal node represents a "test" on an attribute.</br>
We imported sklearn library for accessing the decision tree model.</br>
We trained a decision tree classifier to classify the suicide rate into high or low based on the input data.
# Evaluation
We imported accuracy score and confusion matric from sklearn library to calculate accuracy.</br>
The decision tree has been trained. We evaluated its performance using the accuracy score.</br>
The training accuracy is 100%. We evaluate the model using the validation set.</br>
The validation set accuracy is about 88%, which is better than always predicting "low".</br>
# Hyperparameter Tuning
Next, we tuned some hyperparameters to see if we can improve the accuracy of the model on the validation set.

One common problem of decision tree is that it tends to overfit the training data. In our case, the training accuracy is 100%, which basically means that the model has memorized all the train data (=overfitting). In order to make the model generalize better to unseen data, let's try to tune two hyperparameters.

max_depth: controls the overall complexity of a decision tree (adequate assuming that the tree built is symmetric)</br>
min_samples_split: minimum number of samples required to split an internal node</br>
The optimal hyperparameter combination is max_depth of 34 and min_samples_split of 2. We evaluated the performance of this model on test set.</br>
The test set accuracy score is pretty good at about 91%! Let's save our model (including weights, hyperparameters) so we do not need to retrain the model from scratch every time we need to use it.</br>
# Save Trained Model
We used joblib module to save and load Python objects on the disk.
# Make Prediction on New Inputs
We loaded our decision tree model back using joblib.load.</br>
We defined a helper function to make predictions on new inputs.
# Result
We have used Chi-Square test to find the objective of our project.</br>
The hypothesis statements for the test are:</br>
H0: Suicide rate is independent on age group</br>
H1: Suicide rate is dependent on age group
