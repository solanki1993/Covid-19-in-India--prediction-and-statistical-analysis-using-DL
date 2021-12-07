# Covid-19-in-India--prediction-and-statistical-analysis-using-DL
Context
Coronaviruses are a large family of viruses which may cause illness in animals or humans. In humans, several coronaviruses are known to cause respiratory infections ranging from the common cold to more severe diseases such as Middle East Respiratory Syndrome (MERS) and Severe Acute Respiratory Syndrome (SARS). The most recently discovered coronavirus causes coronavirus disease COVID-19 - World Health Organization

The number of new cases are increasing day by day around the world. This dataset has information from the states and union territories of India at daily level.

State level data comes from Ministry of Health & Family Welfare

Testing data and vaccination data comes from covid19india. Huge thanks to them for their efforts!

Update on April 20, 2021: Thanks to the Team at ISIBang, I was able to get the historical data for the periods that I missed to collect and updated the csv file.

Content
COVID-19 cases at daily level is present in covid_19_india.csv file

Statewise testing details in StatewiseTestingDetails.csv file

Travel history dataset by @dheerajmpai - https://www.kaggle.com/dheerajmpai/covidindiatravelhistory

Acknowledgements
Thanks to Indian Ministry of Health & Family Welfare for making the data available to general public.

Thanks to covid19india.org for making the individual level details, testing details, vaccination details available to general public.



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
