# timeseries
1. load data
2. split into train/test by time


3.1. train scaler_x on the x_train (use StandardScaler!) 


3.2. train scaler_y on the y_train


4.1. Apply scaler_x to x_train and x_test => x_train_scaled, x_test_scaled 


4.2. Apply scaler_y to y_train and y_test => y_train_scaled, y_test_scaled


5. Make TimeseriesGenerator for x_train_scaled and y_train_scaled for the window=168 => x_train_window, y_train_window 


6. Train https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html using x_train_window as inputs and y_train_window as target => model


7. Compute predictions of the model for scaled datasets => pred_train_scaled, pred_test_scaled


8. Reverse predictions using function inverse_transform for the scaler => pred_train, pred_test


9. Compute evaluations: MSE and MAPE


