# Capstone-Project-2--Regression

# Problem Statement: 
Rossmann operates over 3,000 drug stores in 7 European countries. Currently, Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. With thousands of individual managers predicting sales based on their unique circumstances, the accuracy of results can be quite varied. You are provided with historical sales data for 1,115 Rossmann stores. The task is to forecast the "Sales" column for the test set. Note that some stores in the dataset were temporarily closed for refurbishment.

# Introduction
The demand for a product or service always keeps changing from time to time. No business can improve its financial performance without estimating customer demand and future sales of products/services accurately. Sales forecasting refers to the process of estimating demand for or sales of a particular product over a specific period of time. Predicting sales performance is one of the key challenges every business face. It is important for firms to predict customer demands to offer the right product at the right time and at the right place. In this project the machine learning model such as Linear Regression is used to predict future sales.

The dataset consists of two parts. One part is historical daily sales data of each store from 01/01/2013 to 07/31/2015. This part of data has about 1 million observations and 9 columns with no null values. Data included multiple features such as Store, DayOfWeek, Customers, SchoolHoliday, StateHoliday etc. that impact sales. The second part of dataset is supplement store information. It has 1115 store info entries, which listed the store type, competitor informations and a different kind promotions information. It totally consists of 10 columns and a lot of missing values in a few columns. The data types were of integer, float and object in nature in both the datasets.

In this, an effort has been made to analyse and find all the features that are contributing to higher sales and the features which are leading to lower sales, so that improvement plans can be worked upon by using machine learning linear regression model.

# Approch
The approach followed for solving real world business problem is listed in below form of events.

1. Main step in solving any real world problem in data science field is understanding the given datasets properly. The datasets details is already mentioned above.

2. Data Cleaning and Preprocessing: Handling missing values is an important skill in the data analysis process. If there are very few missing values compared to the size of the dataset, we may choose to drop rows that have missing values. Otherwise, it is better to replace them with appropriate values. In this, the second part of dataset has lot of null values for features like CompetitionOpenSinceMonth, CompetitionOpenSinceYear, Promo2SinceWeek, Promo2SinceYear,PromoInterval. The NaN values in CompetitionOpenSinceMonth and CompetitionOpenSinceYear are replaced by mode of column as it give most occurring month. The NaN values in columns Promo2SinceWeek, Promo2SinceYear and PromoInterval indicates that they may not be participating on promo on that period hence they replaced with zero. Lastly before proceeding further, the two datasets were merged on the common column of ‘Store’ to get everything together for the analysis.

3. Exploratory data analysis- It involves exploring and analyzing the dataset given to find out patterns, trends and conclusions to make better decisions related to the data, often using statistical graphics and other data visualization tools to summarize the results.

Main Libraries to be used:

• Pandas for data manipulation, aggregation

• Matplotlib and Seaborn for visualisation and behaviour with respect to the target variable.

• NumPy for computationally efficient operations The goal here is to explore the relationships of different variables with ‘Sales’ to see what factors might be contributing to the high and low sales numbers.

4. Outlier detection: In statistics, an outlier is a data point that differs significantly from other observations. Outliers can occur by chance in any distribution, but they often indicate either measurement error or that the population has a heavy-tailed distribution. The outliers can be treated by

1.mean/median/mode imputation.

2.Quantile based flooring and mapping.

3.Trimming outliers.

Here the outliers are removed based on IQR method and a “fence” is built outside of Q1 and Q3. Any values that fall outside of this fence are considered outliers. To build this fence we take 1.5 times the IQR and then subtract this value from Q1 and add this value to Q3.

5. Data Manipulation: There features like Competition Open since Month and Year are combined to count in total months since the nearest competition was opened. Similarly done for Promo2SinceWeek, Promo2SinceYear. The important features that contribute to the sales is predicted based on the VIF values and correlation heat map.

6. Data Transformation: The data distribution for CompetitionDistance, CompetionOpen, Sales, and Customers is right skewed hence log transformation is performed on these variables for approximating the normal distribution.

7. Data Scaling : The features varying in degrees of magnitude, range and units. Therefore, in order for machine learning models to interpret these features on the same scale, we need to perform feature scaling.For interpreting these features on the same scale, the standardization scaling technique is used.

8. Modeling: The categorical variables cannot be fed into machine learning algorithm directly, hence one hot encoding is performed on these varibles. The dataset is split into test and train data set by considering the test size to be 20% of total dataset. The performance of linear regression algorithm is evaluated using R2-Square and Adjusted R2-Square.

# Conclusions
1. Sales and Customer scatter plot showed a direct positive relation between them.
2. most of the stores have competation distance in the range 0-10 kms, indicates that the competitor stores weren't that far each other. The stores which are not from each other saw more sales than stores located far away indicating competition in busy locations vs remote locations.
3. Storeype b has highest avaerage sales compared to other storetypes.The reasons include all three kinds of assortments specially assortment level b which is only available at type b stores.
4. Upon analysis on the given dataset, it can be established the model developed is able to explain 89.5878 % of the variations.
