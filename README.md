# Air Traffic Forecast
Time Series Analysis on Air Traffic and Cargo System Forecasting

## Data Overview
* Time Period: 1998/01 ~ 2019/10 (Unit: Month)
* Content:
  * Aircraft: Landing, Take-off, Total (Landing + Take-off) and Year-on-year Growth (Total)
    * Use Aircraft Total as example
  * Passenger: Arrival, Departure, Total (Arrival + Departure) and Year-on-year Growth (Total)
  * Freight: Unloaded, Loaded, Total (Unloaded + Loaded) and Year-on-year Growth (Total)

## Data Preparation
* Data Split
  * Training Set: 75% of the full data (1998/01 ~ 2014/04)
  * Validation Set: 25% of the full data (2014/05 ~ 2019/10)
  * Use training set to fit the model and make predictions, then compare the predicted values with validation set.
* Seasonality: Repeating cycle at specific time-frames.
  * Yearly cycle exits in current case.
  * Add seasonal component into the model.

## Model Applied
* Autoregressive Integrated Moving Average (ARIMA)
  * Use 3 parameters to help model the trend and noise of a times series.
  * Shortcoming: Do not support seasonal data.
* Seasonal Autoregressive Integrated Moving Average (SARIMA)
  * An extension of ARIMA that explicitly supports univariate time series data with a seasonal component.
* Training Time: Within 5 mins for each model

## Add External Variables - Holiday Factors
* Data: Public Holidays
* Date Range: 1998/01 ~ 2020/12
* Data Preprocessing: Create structured matrix
  * is_long_weekend: Whether there is any long weekend or not in each month.
  * long_weekend_count: How many long weekends in each month.
  * holiday_count: The number of holidays in each month.
  * is_summer_winter_vacation: Whether specific month is summer/winter vacation or not.
  * long_weekend_length_0 ~ 5: The length of each long weekend. Represented by dummy variables.

## Forecast Result and Performance
<table>
    <tr>
        <td><strong>R-squared</strong></td>
        <td><strong>RMSE</strong></td>
        <td><strong>MAPE</strong></td>
    </tr>
    <tr>
        <td>0.531004</td>
        <td>997.022215</td>
        <td>1.902974%</td>
    </tr>
</table>

***
Copyright © 2020 [Andy Lin](https://github.com/andy2167565). All rights reserved.
