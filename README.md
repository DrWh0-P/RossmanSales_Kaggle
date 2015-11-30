# RossmanSales_Kaggle
FILE DESCRIPTION
Feature_engineering.R
This code can be used to create new features for our data set
I have created the following new features
1.Promo2.Status- whether the Promo2 is active on that particular sale date
2.Competitor.Present-whether a competitor was present on the sale data
3.Weeks.Since.Competitor- no of weeks since the competitor has been active( derived from sale date and CompetitorSince fields)
4.Weeks.After.Promo2- no of weeks passed since the most recent Promo2 reset. Found that the 0,4,5 and 9 weeks after Promo2 reset had high sales. So put those weeks into a bucket for linear regression.
5.Week.Of.Month- week of the month
6. State- state to which the store belongs to
Notes: I tried to get weather data for each state(usign weatherData package) but it was mising information for lot of dates in 2014. So if anybody can get a good source of weather data for each day in 2014,2015 that would be awesome. I didn't try GDP because we dont have 2014 data and population didn't make much of difference so ommitted that.

Data_Source.R
This code does all the data cleaning and merging part. Removed rows with zero sales. Creates seperate files for linear regression and other models

models_revised.R
This code implements all the models. The data was divided into 2 sets-training and evaluation sets. The evaluation set will be used to train adaboost for ensembling.
The predictions from the first 3 models on eval set would be added back to eval set as new features and xgBboost will be used to train the ensemble,
1. Random Forest- uses the H20 package(good for multicore processing)
2. XGboost- uses xgboost package
3. Linear regression- a regression model for each store
4. Xgboost/Weighted Average for esnsembling- 

Notes: random forest and xgboost gave me kaggle scores of almost .11 and linear regression of .16. I haven't tried submitting the ensembling results yet.
Lasso regression wasn't too helpful. 
