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
