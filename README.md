# ML_Project13-ForecastingUsingARIMA

### Forecasting Champagne Sales with ARIMA: A Seasonal Approach
This project explores the use of ARIMA (Autoregressive Integrated Moving Average) models for forecasting monthly champagne sales data. The focus is on capturing the inherent seasonality present in the data.

### Data Acquisition and Preprocessing:

The project utilizes the perrin-freres-monthly-champagne.csv dataset containing historical sales data.

Pandas is used to load and manipulate the data.

Data cleaning involves handling missing values using dropna().

Columns are appropriately named (Month, Sales).

The Month column is converted to datetime format for time series analysis using pd.to_datetime.

The time series is set as the index using set_index('Month').

### Visualizing the Time Series:

The time series data is plotted to observe trends and potential seasonality.

### Testing for Stationarity:

The Augmented Dickey-Fuller (ADF) test is employed using statsmodels.tsa.stattools.adfuller to assess stationarity.

The null hypothesis (H0) assumes non-stationarity, while the alternative hypothesis (H1) suggests stationarity.

The initial test result indicates non-stationarity (presence of a unit root) in the sales data.

### Differencing for Stationarity:

Differencing is applied to transform the non-stationary data into a stationary form.

Two types of differencing are performed:

Regular differencing: df['Sales First Difference'] = df['Sales'] - df['Sales'].shift(1). This captures short-term trends.

Seasonal differencing: df['Seasonal First Difference'] = df['Sales'] - df['Sales'].shift(12). This considers seasonal patterns (e.g., yearly differences).

### Verification of Stationarity:

The ADF test is re-run on the seasonally differenced data (df["Seasonal First Difference"].dropna()) to confirm stationarity.

The test result confirms that the seasonally differenced data is stationary, making it suitable for ARIMA modeling.

### ACF (Autocorrelation Function) and PACF (Partial Autocorrelation Function) Analysis:

Plots of the ACF and PACF (statsmodels.graphics.tsaplots.plot_acf and statsmodels.graphics.tsaplots.plot_pacf) are generated for the seasonally differenced data to identify potential model parameters (p, q) for the ARIMA model.

### ARIMA Model Selection (Next Steps):

Based on the ACF and PACF plots, appropriate values for the ARIMA model's autoregressive (p) and moving average (q) terms will be determined. The seasonal component (P, Q) will also be considered for the seasonal ARIMA model.

The chosen ARIMA model will be fit to the training data, and its performance will be evaluated on unseen test data.
