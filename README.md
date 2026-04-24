# Predictive-Paradox-Electricity Demand Forecasting
# IITG.ai
Recruitment task  for the AI club.
A robust machine learning pipeline to forecast next-hour electricity demand using historical load, weather conditions, and macroeconomic indicators
This project tackles real-world challenges such as noisy data, temporal dependencies, and feature engineering under strict constraints 

The goal:

Predict next hour demand (t+1) using only information available up to time t
#Dataset
Power Demand Data → Hourly grid demand (target variable)
Weather Data → Temperature, humidity, precipitation
Economic Data → Annual macroeconomic indicators
# 1. Data Preparation
Removed duplicate timestamps
Resampled to uniform hourly frequency
Interpolated missing values
Applied rolling median-based anomaly correction (leakage-free)
#2. Feature Engineering

To enable non-sequential models to understand time:
# Time Features
Hour, day of week, month
Weekend indicator
Cyclical encoding (sin/cos transformation)

# Lag features:
Short-term → (t-1, t-2, t-3)
Daily → (t-24, t-48)
Weekly → (t-168)

# Rolling Statistics
Rolling mean and standard deviation (6, 12, 24 hours)

# 3. Data Integration
Merged yearly economic indicators with hourly data using calendar year

# 4. Model
Used XGBRegressor.Its key features:

# 5. Validation Strategy
Strict chronological split
Training: Past data
Testing: Future data (2023 onward)
Ensures zero data leakage

# 6. Evaluation Metric
MAPE (Mean Absolute Percentage Error)
Robust implementation to handle near-zero values

# Results
Achieved a strong MAPE score on unseen future data
Model successfully captures:
SDaily demand cycles
Weekly patterns
Weather-driven variations

# Feature Importance and Prediction Plot

## I obtained MAPE score of 0.104 initially,but when I tried to improve the model by using XGBRegressor,I messed up the indexing,which after fixing gave me a MAPE score of 0.18
## Now that deadline has extended to 3 am,I have implemented XGBRegressor and this thime I got MAPE score of 2.75%!!!
### Very happy with learnings that I got while doing this task,it was nothing less than an advemture!
