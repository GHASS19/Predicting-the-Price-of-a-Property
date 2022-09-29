# Predicting the Price of a Property

## Home Evaluation Predictor 

![image](https://lh3.googleusercontent.com/p/AF1QipMonHBuOOrL0UUzj45iIrfMqY2I76lbLNuPtNFg=w960-h960-n-o-v1)

   *Real Estate companies need help in accurately predicting the price of a home for their clients. They do this with variables such as square feet, bedrooms, etc..  Both the realtor and client need to know if a house is accurately priced. Or over/undervalued. It can help a company assist their clients better. It also gives them a competive advantage over other real estate brokers by providing accurate price predictions.*
 
 
## 1. The Data
The database is the largest collection of quarterback data on Kaggle, (https://www.kaggle.com/datasets/speckledpingu/nfl-qb-stats). The stats are from every National Football League game from 1996-2016. This was a CSV file.
 
## 2. Data Wrangling
[Data Wrangling](https://github.com/GHASS19/QB_Project/blob/main/Notebooks/2.%20QB_Data_Wrangling.ipynb) 
 
In this part of the data exploration I added rows and corrected the columns. I cleaned some of the data and found key features of each column. I found the standard deviation and median. I also discovered if any of the columns had a null value. 
 
There were 719 missing values for the TD per completion and yards per catch columns. It was 5.45% of their entire column for both of these variables. This phase of the project ensured that the data was pure and ready for modeling.
 
## 3. Exploratory Data Analysis
[EDA](https://github.com/GHASS19/QB_Project/blob/main/Notebooks/3.%20QB_EDA.ipynb)
 
I continued to clean up the data to give us a better set of data to work with. More importantly, we found out which variables have a strong & negative correlation.
 
The strongest correlations were Attempts & Completions (.94), Attempts & TDs (.87), Completions & Yards (.91), Attempts & yards (.87), Sack & loss_yds (.91), Yards per Catch & Yards per Attempt (.87) and TD per Attempt & TD per completion (.97).
 
The largest negative correlations were Game Points & Sack (-.23), Game Points & Loss yards (-.23), Interceptions & Rate (-.44) Game Points & Int (-.23). Three of these included game points. Which would be very useful to a team as the more points you score the better odds you have of winning.
 
![image](https://user-images.githubusercontent.com/86930309/182245708-801824a2-5d4e-4c41-8fc5-3bd26f381edb.png)
 
The distribution of the data showed us that many of the touchdowns thrown were in the range of 0-3. There were not many 4-7 touchdowns thrown in a game. Very hard to do. The distribution displayed also that most QBs had a rating of 80 and most of the other data points were equally distributed on either side.
 
 
## 4. Data Preprocessing & Training
[Data Preprocessing & Training](https://github.com/GHASS19/QB_Project/blob/main/Notebooks/4.%20QB%20Data%20Pre-processing%2C%20Training%20and%20Modeling%20Data%20Development.ipynb) 
 
In this section we tried four different models to see which one predicts the y variable the best in the test data. Our y variable is the amount of touchdowns a QB will throw in any given game. The X variables are the rest of our data columns. These different models used the X variable to predict the amount of touchdowns.
 
This was a regression problem as touchdowns in a game is a continuous quantity. I did a train test split on the data to see how accurate each of the four models I examined performed on the data. The four models I tried were linear regression, lasso regression, ridge regression and random forest regression. The best performing model was random forest regression.
 
The Random Forest R2 score was nearly perfect at .997. It had a very solid MAE of .006 and RMSE of .06 on the test data. The CV average & Grid Search CV for Random Forest was a very high score of .9977 and .9979.
 
 
## 5.Recommendations and Going Forward 
 Metrics in the NFL is an interesting concept. There are many variables that we cannot quantify, like a player’s will and determination at any given moment. The future is hard to predict. This random forest model to predict touchdowns a QB will throw is very helpful in understanding what could potentially happen in a game. It gives us a chance to comprehend how a player might do. The more information the better we can make decisions.
 
I would run models on every stat we have on defense, special teams and offense to predict how every player might perform at each position. This would help to evaluate free agents and our own players. We could improve on who to sign in the off-season.
We should also run analytics on situational football. Finding out the probability of converting a first down on a 4th & 2 from our 26th yard line would be beneficial to the coach making a decision to go for it or not. These two ideas could potentially lead to more wins and revenue for the organization.
 
