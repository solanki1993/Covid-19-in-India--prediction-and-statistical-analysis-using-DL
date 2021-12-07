# Covid-19-in-India--prediction-and-statistical-analysis-using-DL
LSTM analysis including its helper functions, Pandas Profiling, plotting of the time series, Exponential Smoothing, Simple Exp Smoothing, Holt, Augmented Dickey Fuller test.


Used pandas profiling to get a better sense of data.

Plotted time series of 3 Variables.
1.Cases
2.Deaths
3.Cured

Resampled number of cases by:
1.Weekly data
2.Monthly data

Setting up helper functions for forecasting
1.get_n_last_days : Extract last n_days of a time series.
2.plot_n_last_days : Plot last n_days of a time series
3.get_keras_format_series : Convert a series to a numpy array of shape [n_samples, time_steps, features]
4.get_train_test_data : Utility processing function that splits an hourly time series into train and test with keras-friendly format, according to user-specified choice of shape.

arguments
1.df (dataframe): dataframe with time series columns.

2.series_name (string): column name in df.

3.series_days (int): total days to extract.

4.input_days (int): length of sequence input to network.

5.test_days (int): length of held-out terminal sequence.

6.sample_gap (int): step size between start of train sequences; default 5

returns
tuple: train_X, test_X_init, train_y, test_y

Defined model architecture: LSTM

Fit LSTM to data train_X, train_y .

arguments

1.train_X (array): input sequence samples for training.

2.train_y (list): next step in sequence targets.

3.cell_units (int): number of hidden units for LSTM cells.

4.epochs (int): number of training epochs


TO Make predictions:
Functions used:

1.predict : Given an input series matching the model's expected format generates model's predictions for next n_steps in the series.

2.predict_and_plot: Given an input series matching the model's expected format generates model's predictions for next n_steps in the series, and plots these predictions against the ground truth for those steps

arguments:

1.X_init (array): initial sequence, must match model's input shape.

2.y (array): true sequence values to predict, follow X_init.

model (keras.models.Sequential): trained neural network.

title (string): plot title.


Decomposed the Time series.
Any time series has 3 components associated with it:

1.Trend
2.Seasonality
3.Residual

did the Augmented Dickey Fuller test (ADF Test) is a common statistical test used to test whether a given Time series is stationary or not.

computed the single MSE, double MSE and triple MSE to compare the results of the 3 statistical models.
