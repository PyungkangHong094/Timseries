# CSE353_ML: Ensemble of LSTM and ARIMA using Time Series

# Introduction
We implement our Time Series Prediction model to predict the future values for NYC taxi passengers from 2014 July to 2015 January. Each model takes training and testing data sets from NUMENTA data set and divided 80% 20% training and testing respectively.

# Background
We used two of the well-known time series models, LSTM and ARIMA. Our goal is to combine those two models, to support each other in terms of accuracy. Our final result kindly shows a bit of higher accuracy compared to using just one model. 

# Code Structure
Our code structure is divided into two big parts of ARIMA and LSTM and at the end the ensembled model. 
1) Each model has a similiar strategy in terms of data preprocessing and spliting the data sets into training and testing.
2) For ARIMA and LSTM we used window size as 168, since we have an hourly timestamps and for a week. (24 * 7 =168)
  - We tried both one week (168) and two weeks(336) and based on the accuracy result, we have chosen the window size 168.
3) For ARIMA, it uses TimeSeriesGenerator to make a window size instead of defining ARIMA(p,d,q) in usual ways.
4) For LSTM, it also uses TimeSeriesGenerator to make a window size.
5) After building a window size, for ARIMA, it uses LinearRegression to train the model and predict.
6) ARIMA MAPE (Mean Absolute Percentage Error): 11.2892
- MAPE: The mean absolute percentage error (MAPE), also known as mean absolute percentage deviation (MAPD), is a measure of prediction accuracy of a forecasting method in statistics, for example in trend estimation, also used as a loss function for regression problems in machine learning. It usually expresses the accuracy as a ratio defined by the formula:


7) For LSTM, it uses Keras, LSTM, to train and predict the model with different layers.
8) LSTM MAPE: 10.0213

# For the ensemble: 
1) First we tried is to average the model.
2) Second trial is to weight more on the accurate model with is LSTM as 80% and 20% manually
3) Finally, we figured out how to weight more on the accurate model without defining the percentage.

- Using MAPE, Weights for ARIMA = (lstm_mape/(arima_mape+lstm_mape)

- Using MAPE, Weights for LSTM = (arima_mape/(arima_mape+lstm_mape)

