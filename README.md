# Predicting the Price of a Property

## Home Evaluation Predictor 

![image](https://lh3.googleusercontent.com/p/AF1QipMonHBuOOrL0UUzj45iIrfMqY2I76lbLNuPtNFg=w960-h960-n-o-v1)

   *Real Estate companies need help in accurately predicting the price of a home for their clients. They do this with variables such as square feet, bedrooms, etc.  Both the realtor and client need to know if a house is accurately priced. Or over/undervalued. It can help a company assist their clients better. It also gives them a competive advantage over other real estate brokers by providing accurate price predictions.*
 
 
## 1. The Data
The data is a CSV from a Seattle metro area real estate database on kaggle, (https://www.kaggle.com/datasets/shree1992/housedata?select=data.csv ). The data timeframe is from May 1st, 2014 to July 9th, 2014.
 
## 2. Data Wrangling
[Data Wrangling]([https://github.com/GHASS19/QB_Project/blob/main/Notebooks/2.%20QB_Data_Wrangling.ipynb](https://github.com/GHASS19/Predicting-the-Price-of-a-Property/blob/main/Notebooks/Data%20Wrangling%20%26%20EDA%20for%20Home%20Price%20Predictor%20Capstone.ipynb)) 

I initially had 4,600 rows and 18 columns from the kaggle dataset. During this stage I uploaded the data to a jupyter notebook. Cleaned the data such as separating the column ‘StateZip’ into a separate ‘State’ and ‘Zip Code’ columns. Added the rows ‘bd/bd %’, (Bedrooms / Bathrooms) and 'Age’ (Year -  Yr_built).

I rearranged the columns to put relevant variables next to each other and explored the mean, maxim, minimum, standard deviation of each numeric column. This helped to understand my data and see if there were any missing values or outliers.

## 3. Exploratory Data Analysis
[EDA](https://github.com/GHASS19/QB_Project/blob/main/Notebooks/3.%20QB_EDA.ipynb)
 
I continued to clean up the data to give us a better set of data to work with. More importantly, we found out which variables have a strong & negative correlation.
 
The correlation heat map was very useful to see which columns were relevant. There were a few variables that had a high positive correlation:
1. Square feet of living and square feet above are related at .88.
2. Square living space and bathrooms had a high correlation at .76.
3. Square living space above and bathrooms also have a high correlation at .69.

Negitive Correlation:

1.The biggest negative correlation was bed to bath ratio at -.66.

 ![image](https://user-images.githubusercontent.com/86930309/193145314-8b8c26b4-0fa3-44d7-914d-2b8dcfcd7a77.png)

Other interesting finds during the EDA stage was:
- There was many outliers with a high amount of square feet for living, above and below ground level.
- The majority of homes that were sold had a good condition rating of 3-5.
- As the number of bedrooms increased so did the amount of bathrooms in a particular house increase too. 
- Most of the homes had between three and six bedrooms.
- There was a positive correlation between price and square feet of living space. 
- One home had a square feet of living space that was under 2,000 sq ft and was very expensive. 
 
## 4. Data Preprocessing & Training
[Data Preprocessing & Training](https://github.com/GHASS19/QB_Project/blob/main/Notebooks/4.%20QB%20Data%20Pre-processing%2C%20Training%20and%20Modeling%20Data%20Development.ipynb) 
 
In this section we tried four different models to see which one predicts the y variable the best in the test data. Our y variable is the amount of touchdowns a QB will throw in any given game. The X variables are the rest of our data columns. These different models used the X variable to predict the amount of touchdowns.
 
This was a regression problem as touchdowns in a game is a continuous quantity. I did a train test split on the data to see how accurate each of the four models I examined performed on the data. The four models I tried were linear regression, lasso regression, ridge regression and random forest regression. The best performing model was random forest regression.
 
The Random Forest R2 score was nearly perfect at .997. It had a very solid MAE of .006 and RMSE of .06 on the test data. The CV average & Grid Search CV for Random Forest was a very high score of .9977 and .9979.
 
 
## 5.Recommendations and Going Forward 
 Metrics in the NFL is an interesting concept. There are many variables that we cannot quantify, like a player’s will and determination at any given moment. The future is hard to predict. This random forest model to predict touchdowns a QB will throw is very helpful in understanding what could potentially happen in a game. It gives us a chance to comprehend how a player might do. The more information the better we can make decisions.
 
I would run models on every stat we have on defense, special teams and offense to predict how every player might perform at each position. This would help to evaluate free agents and our own players. We could improve on who to sign in the off-season.
We should also run analytics on situational football. Finding out the probability of converting a first down on a 4th & 2 from our 26th yard line would be beneficial to the coach making a decision to go for it or not. These two ideas could potentially lead to more wins and revenue for the organization.
 
