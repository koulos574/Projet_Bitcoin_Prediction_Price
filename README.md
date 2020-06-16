# Bitcoin Price Prediction
This is the final project of the course "Python for Programming Business" at ESSEC Business School. 
#### Status of the project - Finished (Can be enhanced).

## Introduction/Aim of the project

The purpose of the project is to predict the future price of Bitcoin based on multiples inputs.
The inputs used are the 2018-2020 daily values of :
- Gold
- Ethereum price,
- US Dollar to Chinese Yuan,
- SP 
- Bitcoin Price

### Methods
* Data Manipulation
* Data Visualization
* Machine Learning 
* Time series modelization (ARIMA and VAR)


### Technologies
* Python
* Pandas, Numpy, Matplotlib
* Google Collab, Jupyter Notebook
* Time-Series Analysis (statsmodels)

## Project Description

Given that the aim of the project is to predict a time series (bitcoin prices over time), we tried various timeseries modeling methods to predict it.

In the first notebook (Bitcoin ARIMA), we used a univariate timeseries method called ARIMA. This is a very common model that usually has pretty decent predictions. This model creates a linear equation in order to compute the next value of the series using the previous values and errors The model computes the next value of the series using the last p values of the series, and adjusting the prediction with the last q errors. 

The purpose of this model is to complement the VAR model with a simpler estimate. It also allows the project to test whether complexifying the forecast with additional variables leads to more accurate forecasts - and if so, it allows for a direct comparison in forecast quality.

In order to have a good prediction, the series we used had to be stationnary, meaning it had to have constant mean and variations. To make our series (Bitcoin prices) sationnary, we had to differenciate it, meaning to substract the former value from the next one, as many times as required. In this case, one differenciation was enough, giving us our first parameter : d=1.

The model had a hard time trying predicting short term variations in bitcoin prices (with small p and q). However, when given a large number of former values (large p and q), it had pretty good predictions for up to one month. 
The final model is an ARIMA(50,1,50).
The second notebook (Bitcoin - VAR Model) displays a multivariate timeseries model, the VAR model (Vectorized AutoRegression).

This works in a similar manner to the ARIMA model, to the extent that it computes the next values of a time series using the previous data points. The big difference is that it computes as many time series as we want, and it predicts the future values of all time series at the same time. It predicts all values so that it can make longer-term predictions based on previous prediction of all series. In other terms, the equation predicting the future value of one of the series is calculated on the basis of the previous values of all series.
This second model is the more complex one, and it includes inputs that we thought could be relevant to forecast bitcoin prices.
The inputs included are : 
- The price of gold. This is a stable measure that can inform us on global economic health. Here, we are wondering whether the Bitcoin price is affected by the global economy.
- The S&P, a stock market index measuring the stock performance of 500 large companies in the United States. We are using it as a general indicator of the US's market health. Here, we are wondering whether the Bitcoin price is affected by the US economy.
- The price of Ethereum (ETH), another crypto currency, that we are using as a comparison measure - we are checking whether crypto currencies influence each other 
- The exchange rate between the Dollar and the Yuan, to check whether the health of these currencies and the geopolitical implications impact Bitcoin. 
We initially wanted to include Twitter inputs to give us more qualitative data rather than quantitative, and to showcase the public's opinion as well as experts' opinions. However, we encountered several issues with the retrieval of data, notably the fact that twitter doesn't allow for scapping >100 data points - meaning that we had data covering time periods that were way too short. We attached the Twitter data retrieved and transformed in the file Twitter_data.

## Skills for the project

* Data Exploration
* Data Manipulation
* Machine Learning
* Statistical modeling/knowledge
* Predictive Modeling
* The Willingness To Learn

## Getting Started

1. Clone this repositery (gcl https://github.com/koulos574/Projet_Bitcoin_Prediction_Price)
2. Open Folder in Jupyter Notebook and Run All
3. Have Fun :)

## Files descritpion

| Name                   | Description |
| :---                    | --- |
| Bitcoin - ARIMA.ipynb   | Prediction based on ARIMA (Sarimax)| 
| Bitcoin - VAR model.ipynb       | Data manipulation and visualisation | 
| twitter.ipynb| Sentiment Analysing of Bitcoin tweets|
| Bitcoin - files used| Folder with all data collected and used| 
| Bitcoin Historical Data - Investing.com (1).csv | Bitcoin dataset from 13-05-2018 to 13-06-2020| 
| ETH_USD Bitfinex Historical Data.csv | Ethereum to Dollar dataset from 13-05-2018 to 13-06-2020| 
| USD_CNY Historical Data.csv| US Dollar to Chinese Yuan Renminbi dataset from 14-05-2018 to 12-06-2020 | 
| ^GSPC (1).csv | GSPC dataset from 13-05-2018 to 12-06-2020 | 
| gold-Current.csv| Gold dataset from 04-01-2016 to 29-05-2020|


## Useful links/resources
ARIMA model explanation : https://towardsdatascience.com/time-series-forecasting-a-getting-started-guide-c435f9fa2216#:~:text=An%20exogenous%20variable%20is%20one,we'll%20be%20working%20with.

ARIMA model GitHub : https://github.com/osbarge/salesforecaster/blob/master/unify_data_sources_and_predict.ipynb

VAR model explanation : https://www.machinelearningplus.com/time-series/vector-autoregression-examples-python/?fbclid=IwAR3ISdAeAKsD2cAZQNoCpPsh3fpYKCW52woRLZfarTjxzgXH114DwHBvM1k

Global time series ML methods explanation : https://towardsdatascience.com/recurrent-neural-networks-for-electricity-price-prediction-a26f8411ea44

Global time series ML methods github : https://github.com/Carterbouley/ElectricityPricePrediction

Twitter Sentiment Analysis : https://github.com/cjhutto/vaderSentiment
