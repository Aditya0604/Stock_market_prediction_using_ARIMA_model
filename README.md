# Stock Market Prediction using Arima Model

The motive of the project was to understand and implement an ARIMA model(although I also implemented LSTM as well out of interest) to predict the stock market prices from previous data.
data used from Yahoo Finanace:
1. Reliance data : https://finance.yahoo.com/quote/RELIANCE.BO/history?p=RELIANCE.BO
2. ICICI data: https://finance.yahoo.com/quote/ICICIBANK.BO/history?p=ICICIBANK.BO

In the first week I learned about Python language

then Numpy in the 2nd week

then Pandas in hte 3rd week

then exploratory data analysis in the 4th week and

time series analysis in the 5th and 6th week

and I devoted the last two weeks for the project implementation and work.


Now, I started the project by importing useful python libraries like Pandas, Numpy, Matplotlib, Yahoo Finance, etc. and then reading the data into the collab using read_csv.

Then I started exploring the data to look for any null values and non numerical data, from which I got to know that the "Date" column is a string and I converted the index of the data into 
the date column values in the timestamp object using the to_datetime function.

Now we only needed the date attributes(which were converted as the index of the data) and the "Close" values in the data, so I created series of all data just using close column values by ICICI_data_6m = ICICI_data_6m["Close"]

# ACF & PACF plots
Then I used statsmodel, statstools to plot the ACF and PACF plots for all the datas

# Checking Stationarity using adfuller test
We cant only train the ARIMA model with stationary data, hence I did adfuller test to check the stationarity and if the p value is >0.05 data is not stationary, so the p values in our data was much greater than 0.05, hence we need to remove the stationarity of the data before proceeding further.

# Differencing
Both, from the graph and from the adfuller test we could see that the data is not stationary, as the p value is quite high, thus we need to make the data stationary first in order to train the model.
Thus to make the data stationary we try differencing (i.e. shift the data) 
now, after we used 1st order differencing, we see that the p value has decreased tremendously and now it is <0.05 So, now, the data is stationary and we can use it to train the ARIMA model.

# Training the model
Before training, we would need to find the best order i.e. the best p,d,q values for the model.For this purpose I would use AUTO ARIMA, which would help me to get the best order for my model and I got the best fit order as (0,0,0) but trying out this order for our model, the results were not satisfactory, and our model did not perform well while fitting the data.

# Experimentation
Now as we used a 1st order differencing, the value of d for our model is 1. so lets try to put d=1 in the best fit order(0,0,0) which will give us the new order as (0,1,0). After trying this new order for our model, our model performed quite well, It nicely fitted the values and gave a nice graph. So we would continue with this order value for all of the data

# Train & Test Split
Now I decided to split the data into training and test set to train and evaluate the model.
So, I split the last 30 values of the data into test set and the remaining values as the training data.

Now I used the model to predict the values for the test data and used the following evaluation metrics like mean square error, mean absolute error, RMSE, mean avg. percentage error to see how our model has performed as well as I have also plot the graph of aur actual test values vs what our model predicted.

However as the model was trained on the differenced data. The model also predicted differenced values, hence to convert the differenced value into the scale of original input data, I had to use the cummulative sum of values(which does the opposite effect of differencing). and add to it the first value of the data, so as to get the values in the original scale.

# The End
So I was successfully able to implement a ARIMA model that predicts the price of stocks based on previous data.





