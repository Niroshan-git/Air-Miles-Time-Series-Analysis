# Air Miles Prediction Analysis using Holt Winters Method

This project analyzes and forecasts monthly air miles data using the Holt Winters Triple Exponential Smoothing method. The analysis includes exploratory data analysis, seasonal decomposition, and future predictions.

## Dataset

The dataset contains monthly air miles data from January 1996 to May 2005 (113 entries). The data is structured with two columns:
- Date (index): Monthly timestamps
- Y: Number of air miles

## Requirements

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.graphics.tsaplots import month_plot, quarter_plot
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
from statsmodels.tsa.seasonal import seasonal_decompose
from statsmodels.tsa.holtwinters import SimpleExpSmoothing, ExponentialSmoothing
from sklearn.metrics import mean_absolute_error, mean_squared_error, mean_absolute_percentage_error
```

## Data Preprocessing

1. Load the data from 'airmiles.csv'
2. Set the date column as index with monthly frequency ('MS' - Month Start)
3. Rename the target variable to 'Y'

## Exploratory Data Analysis

The analysis includes several visualizations:
- Monthly air miles time series plot
- Monthly seasonality plot
- Quarterly seasonality plot
- Seasonal decomposition (multiplicative model with period=12)
- Autocorrelation (ACF) plot
- Partial Autocorrelation (PACF) plot

## Model Development

### Training and Test Split
- Training data: January 1996 to May 2004
- Test data: Last 12 months (June 2004 to May 2005)

### Holt Winters Triple Exponential Smoothing
Model parameters:
- Trend: Multiplicative
- Seasonal: Multiplicative
- Seasonal Periods: 12 months

## Model Performance

The model achieved the following metrics on the test set:
- Mean Absolute Error (MAE): 877,575.16
- Root Mean Square Error (RMSE): 1,075,653.07
- Mean Absolute Percentage Error (MAPE): 1.80%

## Future Predictions

The model was then used to forecast air miles for the next 12 months (June 2005 to May 2006). Here are the forecasted values:

```python
2005-06-01    53,177,050
2005-07-01    55,856,840
2005-08-01    55,599,800
2005-09-01    43,746,280
2005-10-01    49,228,220
2005-11-01    46,559,350
2005-12-01    48,857,960
2006-01-01    44,294,770
2006-02-01    43,671,900
2006-03-01    53,977,460
2006-04-01    51,125,200
2006-05-01    51,788,270
```

![image](https://github.com/user-attachments/assets/16662826-41ee-449e-a950-68f1ca515c06)

![image](https://github.com/user-attachments/assets/4699d6d2-ebfe-4c8b-84df-e215a745764b)

![image](https://github.com/user-attachments/assets/c0f1fa12-605f-491f-a74e-0a2ab4000b0c)

![image](https://github.com/user-attachments/assets/7e3e5223-af2b-4e86-aaa9-47277fc6f3dc)


## Notes

- The model shows a convergence warning which might indicate that the optimization process didn't fully converge
- The low MAPE (1.80%) suggests that the model performs well despite the convergence warning
- The predictions maintain the seasonal pattern observed in the historical data

## Future Improvements

1. Try different seasonal periods
2. Experiment with additive trends and seasonal components
3. Implement other forecasting methods for comparison
4. Add cross-validation for more robust error estimation
5. Analyze and handle the convergence warning

## Repository Structure

```
├── airmiles.csv           # Raw data
├── analysis_notebook.py   # Python script with analysis
└── README.md             # This file
```
