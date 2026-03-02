Biomass Demand Forecasting (2018–2026)
This project implements a machine learning pipeline to predict biomass availability/demand across various geographical coordinates using LightGBM. It transforms historical wide-format data into a time-series ready format and employs recursive forecasting to predict values through 2026.
🚀 Overview
Target: Predict Biomass levels based on historical trends and location.
Model: LightGBM Regressor.
Horizon: 2018 to 2026.
Key Techniques: Wide-to-long data melting, Lag features, Rolling statistics, and Recursive multi-year forecasting.
📊 Dataset Structure
The model expects a CSV (Biomass_History.csv) with the following structure:
Index: Unique identifier for the location.
Latitude / Longitude: Geographic coordinates.
2010, 2011, ... 2017: Yearly biomass values (Wide format).
🛠️ Feature Engineering
To capture temporal dependencies, the following features are engineered:
Lag Features: Lag_1, Lag_2, and Lag_3 (Biomass from previous 3 years).
Rolling Mean: A 3-year moving average to smooth out fluctuations.
Growth Rate: Percentage change from the previous year.
Time Trends: Year and Year_squared to capture non-linear temporal trends.
💻 Installation
bash
pip install lightgbm pandas numpy matplotlib scikit-learn
Use code with caution.

📈 Workflow
Preprocessing: Handles missing values via forward/backward filling and melts data into a long format.
Validation: Trains on data up to 2016 and validates against 2017 to ensure accuracy (RMSE/R²).
Recursive Forecasting:
Predicts 2018 biomass.
Uses the 2018 prediction as a "Lag" for the 2019 prediction.
Repeats this process until 2026.
Visualization: Generates dark-themed trend plots comparing historical data against the forecast.
🏆 Results
The model outputs a final CSV Biomass_2018_2026_Forecast.csv containing:
Index, Latitude, Longitude, Year, and the predicted Biomass.
