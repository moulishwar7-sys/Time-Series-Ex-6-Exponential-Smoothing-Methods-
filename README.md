# Time-Series-Ex-6-Exponential-Smoothing-Methods-

# AIM:
To implement and compare three exponential smoothing techniques for time-series forecasting:

1. Simple Exponential Smoothing

2. Holt's Linear Trend Method

3. Holt-Winters Seasonal Method

# PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.holtwinters import SimpleExpSmoothing, Holt, ExponentialSmoothing

# 1. Simple Exponential Smoothing (Base usage)
base_kwh = [450, 460, 455, 462, 448, 465, 458, 461, 450, 459]
data1 = pd.Series(base_kwh)
model1 = SimpleExpSmoothing(data1)
fit1 = model1.fit(smoothing_level=0.3, optimized=False)
forecast1 = fit1.forecast(3)
print("1. Electricity Base Usage Forecast (SES):")
print(forecast1)

# 2. Holt's Linear Method (Growing usage)
trend_kwh = [450, 470, 495, 510, 535, 560, 580, 605, 630, 655]
data2 = pd.Series(trend_kwh)
model2 = Holt(data2)
fit2 = model2.fit()
forecast2 = fit2.forecast(3)
print("\n2. Electricity Growing Usage Forecast (Holt):")
print(forecast2)

# 3. Holt-Winters Method (Weekly seasonality = 7 days)
weekly_kwh = [
 500, 520, 510, 530, 580, 650, 640, # Week 1
 510, 535, 520, 545, 595, 670, 660, # Week 2
 525, 545, 535, 560, 610, 685, 675 # Week 3
]
data3 = pd.Series(weekly_kwh)
model3 = ExponentialSmoothing(data3, trend="add", seasonal="add", seasonal_periods=7)
fit3 = model3.fit()
forecast3 = fit3.forecast(7)
print("\n3. Weekly Electricity Usage Forecast (Holt-Winters):")
print(forecast3)
```

# OUTPUT:
<img width="425" height="312" alt="image" src="https://github.com/user-attachments/assets/e2802285-041b-4471-9719-6b6d1f755405" />

