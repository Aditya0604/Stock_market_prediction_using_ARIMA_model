# Stock Market Prediction using Arima Model

The motive of the project was to understand and implement an ARIMA model to predict the stock market prices from previous data.
data used from Yahoo Finanace:
1. Reliance data : https://finance.yahoo.com/quote/RELIANCE.BO/history?p=RELIANCE.BO
2. ICICI data: https://finance.yahoo.com/quote/ICICIBANK.BO/history?p=ICICIBANK.BO

Now, I started the project by importing useful python libraries like Pandas, Numpy, Matplotlib, Yahoo Finance, etc. and then reading the data into the collab using read_csv.

Then I started exploring the data to look for any null values and non numerical data, from which I got to know that the "Date" column is a string and I converted the index of the data into 
the date column values in the timestamp object using the to_datetime function.

Now we only needed the date attributes(which were converted as the index of the data) and the "Close" values in the data

