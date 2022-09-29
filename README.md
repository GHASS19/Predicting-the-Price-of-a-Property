# Predicting the Price of a Property

## Home Evaluation Predictor 

![image](https://lh3.googleusercontent.com/p/AF1QipMonHBuOOrL0UUzj45iIrfMqY2I76lbLNuPtNFg=w960-h960-n-o-v1)

   *Real Estate companies need help in accurately predicting the price of a home for their clients. They do this with variables such as square feet, bedrooms, etc.  Both the realtor and client need to know if a house is accurately priced. Or over/undervalued. It can help a company assist their clients better. It also gives them a competive advantage over other real estate brokers by providing accurate price predictions.*
 
 
## 1. The Data
The data is a CSV from a Seattle metro area real estate database on kaggle, (https://www.kaggle.com/datasets/shree1992/housedata?select=data.csv ). The data timeframe is from May 1st, 2014 to July 9th, 2014.
 
## 2. Data Wrangling
[Data Wrangling](http://localhost:8888/notebooks/Documents/GitHub/Home%20Price%20Predictor%20Capstone/Data%20Wrangling%20%26%20EDA%20for%20Home%20Price%20Predictor%20Capstone.ipynb)

I initially had 4,600 rows and 18 columns from the kaggle dataset. During this stage I uploaded the data to a jupyter notebook. Cleaned the data such as separating the column ‘StateZip’ into a separate ‘State’ and ‘Zip Code’ columns. Added the rows ‘bd/bd %’, (Bedrooms / Bathrooms) and 'Age’ (Year -  Yr_built).

I rearranged the columns to put relevant variables next to each other and explored the mean, maxim, minimum, standard deviation of each numeric column. This helped to understand my data and see if there were any missing values or outliers.

## 3. Exploratory Data Analysis
[EDA](http://localhost:8888/notebooks/Documents/GitHub/Home%20Price%20Predictor%20Capstone/%20Pre-Processing%2C%20Training%20%20%26%20Modeling.ipynb#)
 
I continued to clean up the data to give us a better set of data to work with. More importantly, we found out which variables have a strong & negative correlation.
 
The correlation heat map was very useful to see which columns were relevant. There were a few variables that had a high positive correlation:
a. Square feet of living and square feet above are related at .88.
b. Square living space and bathrooms had a high correlation at .76.
c. Square living space above and bathrooms also have a high correlation at .69.

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
[Data Preprocessing & Training](http://localhost:8888/notebooks/Documents/GitHub/Home%20Price%20Predictor%20Capstone/%20Pre-Processing%2C%20Training%20%20%26%20Modeling.ipynb)

## a. Data Preprocessing

In this stage of the project I prepared the data for modeling. I created a new column, ‘Renovation Age’, (Year - Yr_Renovated). I also removed the two NaNs from the ‘bd/ba %’ column and made them 0. They were NaNs since the two homes did not have a bed or bathroom. I also split the ‘Date’ column into ‘Year’, ‘Month’, ‘Day’ , and ‘Week’. I encoded the view and condition columns for three models, Linear Regression, Ridge Regression and XGB Regression. 

I did a 70% train and 30% test split on the data for my four models.

 ## 5. Modeling
 [Modeling](http://localhost:8888/notebooks/Documents/GitHub/Home%20Price%20Predictor%20Capstone/%20Pre-Processing%2C%20Training%20%20%26%20Modeling.ipynb)
 
I tested four different models with a standard scaler on each for my supervised regression price prediction:
 
## a. Linear Regression
The most accurate R2 score on the test data was Linear Regression at .4696. It would be hard to predict the price of a home if you get less than half of them correct. The MSE for Linear Regression was 61,734,606,846.02. The RMSE was 248,464.50 and 164,817.45 MAE for the test data from Linear Regression. All these statistics suggest that this model could be very inaccurate at predicting the price. The cross validation mean scores were slightly lower for the R2 score at .413 and a standard deviation average of .198. The grid search cross validation average was .332 for the R2 score and a standard deviation of .154 for Linear Regression.

## b. Ridge Regression
Ridge Regression was similar to Linear Regression. The R2 test score was slightly lower at .467. The MSE was 61,974,982,112.41, RMSE was 248947.74 and the MAE was 165,587.70. The mean cross validation R2 score was .413 and the standard deviation average was also .198. The grid search mean was .419 for the R2 score and the standard deviation was .195.
.
## c. Random Forest Regression
The Random Forest Regressor model had an R2 test score lower than the first three models at .395. The MSE was also very high at  70,352,537,281.89, RMSE was 248,947.74 and the MAE was 140,215.58. These numbers suggest that it is inaccurate at predicting the price. The cross validation mean R2 score was .358 and the standard deviation was .208. For the grid search the R2 mean score was .276 and a standard deviation of .319. The cross validations confirm that this model is not very good at predicting the price.
 
## d. XGB Regression
The XGB Regression Model had the lowest R2 test score of .303. The MSE was 81,126,092,073.28, RMSE was  248,947.74 and the MAE was 145,701.31. The cross validation mean R2 score was .285 and the standard deviation was .173. The grid search R2 score average was .236 and the standard deviation average was .411. This was the most inaccurate model out of all four.

 
## 6. Recommendations and Going Forward 

## - Recommendations:

a. More Data

That we use more sales data to predict the price of a home. More information on homes that sold could lead to a model that has a higher R2 score and is more accurate at predicting. If there are more variables like garage size and school district could lead to an improved model. If we had the data on sales for every home sold in the Seattle area for an entire year we could potentially create a better model predictor.
 
b. Sharing Information to Clients

I would share with potential clients of the real estate firm the correlations we found from our exploratory data analysis. If they are interested in purchasing a home, we found certain traits that go together. Such as the more square feet a home has, the price typically increases. Thus the buyers would need more money. If a buyer with a large family values space in a home they will likely need more cash for the property. A good thing to mention to clients is that a majority of homes that sell have a condition rating of three or higher. This would help with buyer morale since they know the home could potentially be in a good shape and does not need many repairs. It would also help sellers to realize that they will need to fix issues with the house if they want to go under contract.
 
c. Unique Houses for Clients

If a client was looking to sell a home that had traits that were an outlier in the Seattle area we could compare it to other properties that had similar traits. We could use this data for comps to show a potential seller what they could possibly sell their house for based upon similar homes. The data could also help a buyer know if a house they really like is over or under priced. It could potentially be a better predictor of comps than what is on zillow.
 
## - Going Forward

The company needs to obtain or collect more data to create a better regression model to predict the price of a home for their buyers and sellers. The data department could collect the information from their local Multiple Listing Service or from county documents.The more information we can obtain the better we can help serve our potential clients. This would give us a competitive advantage over other real estate firms.

I also suggest running models on all the variables to help clients. This would help them understand how much square feet of living space you can expect with other independent variables. Or how many bedrooms they could expect with certain X variables.

