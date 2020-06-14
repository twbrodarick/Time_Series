# Yen Forecasting - Time Series Analysis

## Background

The financial departments of large companies often deal with foreign currency transactions while doing international business. As a result, they are always looking for anything that can help them better understand the future direction and risk of various currencies. Hedge funds, too, are keenly interested in anything that will give them a consistent edge in predicting currency movements.

In this project, Time Series Forecasting and Linear Regression Modeling are used to predict future movements in the value of the Japanese yen vs. the U.S. dollar.

## Time-Series Forecasting

Historical Dollar-Yen exchange rate futures data are applied to time series analysis in order to determine whether any predictable behavior.
Steps taken:

1. Decomposition using a Hodrick-Prescott Filter (the Settle price is decomposed into trend and noise).
2. Returns are forecasted using an ARMA Model.
3. Settle Price is forecasted using an ARIMA Model.
4. Volatility is forecasted with GARCH.

## Time-Series Conclusions:

No, I would not buy the Yen despite the expected 5-day increase. The forecasted increase is negligible on a percentage basis and the ARMA and ARIMA model p-values suggest these models are not good fits. The GARCH model does indicate it's a good fit. So I would be willing to bet on volatility increasing to 7.597 in the next 5 days if the futures premium and liquidity allow me to execute a trade calling for such a narrow increase of +2%.


## Linear Regression Forecasting

In this notebook, a Scikit-Learn linear regression model is used to predict Yen futures ("settle") returns with *lagged* Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects) via the following steps:

1. Data Preparation (Creating Returns and Lagged Returns and splitting the data into training and testing data)
2. Fitting a Linear Regression Model.
3. Making predictions using the testing data.
4. Out-of-sample (data the model hasn't seen before) performance.
5. In-sample (data the model was trained on) performance.


* Does this model perform better or worse on out-of-sample data compared to in-sample data?

## Linear Regression Conclusions:

Comparing the two RMSE's, the RMSE from the out-of-sample results is 0.415 compared to 0.566 for the in-sample results indicating the model performs better on the out-of-sample results.

As RMSE reflect the standard deviations of the error around the mean, one would expect the out-of-sample results, which reflect test data, to have a larger RMSE compared to the in-sample results which reflect training data.

One hypothesis why the out-of-sample RMSE is slightly higher is the train data is significantly larger than the test data. Also the train data may reflect the wider dispersion of results than experienced in the test data, which could explain why the RMSE was smaller for the out-of-sample results.

Given the proximity of these values to zero and how closely they approximate each other does suggest our model is stable.