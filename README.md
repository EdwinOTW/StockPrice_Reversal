# Capstone Project-Stock-Price-Reversal-

In this project, my objective is the to use the best model to predict and classify reversal points at this moment.

# Problem Statement

In the financial markets, traders have always said, Buy low and Sell High (Motto of the Century)
However, the problem that everyone faces in the investing/ trading world is, at any given moment, we are all questioning, is this really the lowest price now and we should buy the stock now / is this really the highest price now and we should sell the stock to take profit or short the stock?
In this project, I am going to solve this problem and identify the reversal points (buy/sell points) for a few selected stocks.

# Summary of Process

First we had to scrape the stock data from Yahoo Finance. From there our dataset would consist of High price, Low price, Open price, Close price, Volume and Time.
The idea is to use regreession technique to forecast the price of the individual stock. Then using a function to classify whether each point in time is a reversal point, or not. If it is a reversal point (1), I will buy the stock. If it is a reversal point (2), I will sell the stock. If not, hold.
My dataset had 10060 observations and 8 features after I created reversal and gain columns. Reversal column is the target and the others are features.

Multiple Models were created and the best one was selected. Using the parameters of the best model, I created 1 model for each stock that I am analyzing.

# Process

After the data was collected and Labeled, Exploratory Data Analysis was performed to see the accuracy of the reversal point function. ADfuller Test was performed to test for stationarity of the features.
From there, additional features were created.

After initial feature engineering, I ran a function to create features for 70 different technical indicators for me to us in the prediction.
Total number of features: 80

For the first try, I attempted to use Classification Models to directly predict reversal points using the features created.

Next, I using Regression Models to forecast the close price. Then using the reversal function to classify the reversal points before checking the predicted reversal points with the actual using a confusion matrix.
Models Tested: LassoCV, Random Forest, AdaBoost, Gradient Boost, SVM, XGBoost, ARIMA, SARIMA
Final Model Used: SARIMA

# Conclusion

In this project, I selected the best SARIMA model because the machine learning models does not seem to be very efficient in forecasting the prices properly even though some of the models have low RMSE scores. XGBoost and lassoCV Model have about 20 RMSE, however, it can be seen that the model's predicted values is only just following the actual price but with a lag of 10 periods. It is unable to do actual forecasting. Hence, I decided to go with SARIMA model.
SARIMA is able to forcast for about 10 to 15 periods before being unable to forecast any more price changes. Although it is not the best model as it would not be able to capture any sudden huge prices changes, at the moment it is still able to achieve what I would like to achieve, which is to forecast prices 13 periods ahead.
Using the forecasted prices, I am able to pinpoint current reversal point.

# Future Work

- Deployment of Model
- Improve Forecasting Model
  - SARIMAX + GARCH
  - Using Fundamentals as features 
  - Sentiment Analysis on the News Deep Learning Models
- Create Evaluation Metrics to evaluate Model
- Use different GridSearch Metric (AIC, BIC)
