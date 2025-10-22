# U.S. Traffic Accident Analysis (2016–2023)
Read the full report at https://drive.google.com/file/d/1WyM_XLCv-avkHU21p_NsMnJwWKvVdCaU/view?usp=sharing
## Overview
This project explores over 7 years of U.S. traffic accident data (2016–2023) to uncover what factors most strongly influence accident severity. Using both Tableau visualizations and Python-based statistical modeling, we investigate how geographic, weather, temporal, and infrastructural factors contribute to the likelihood and intensity of accidents across states.

The dataset comes from Kaggle’s U.S. Accidents Dataset and contains features such as:
- Severity (1–4, least to most severe)
- Time & Location (latitude, longitude, timestamp)
- Weather (temperature, precipitation, visibility, wind speed)
- Road Features (traffic signal, crossing, junction, etc.)
## Part 1: Exploratory Analysis & Tableau Visualizations
We began by addressing four guiding questions:
- Which states are most accident-prone?
- How does weather affect accident severity?
- When do severe accidents occur most often?
- Which road features see the most accidents?
These insights were visualized in Tableau dashboards to highlight state-by-state comparisons, weather conditions, and time-of-day trends.
## Part 2: Statistical Modeling & Predictive Analysis
After initial exploration, we focused on one central question:
- What factors most influence accident severity?
  
**Linear Regression**

We built a multiple linear regression model with predictors including State, Road Features, Weather Variables, and Time of Day.
- Achieved R² = 0.244, meaning 24% of severity variance was explained.
- Model assumptions (normality, independence) were partially violated due to data imbalance, leading to further refinement.
  
**Logistic Regression**

To model severity as a binary classification (e.g., severity > 2), we trained logistic regression models using weather-related predictors only.
- Precipitation emerged as the strongest positive predictor of accident severity.
- Low pressure and high distance traveled also correlated with more severe accidents.
  
**Tree-Based Models (LightGBM, XGBoost, Random Forest)**

To capture non-linear patterns, we trained tree-based regressors on a balanced sample of the dataset.
Top Predictors (LightGBM & XGBoost):
- Distance from city center – proxy for rural vs. urban environment and EMS response time.
- Travel distance (Distance_Score) – longer trips correlate with higher speeds and risk.
- Pressure, Wind Chill, Humidity, Hour – capture weather and rush-hour patterns.
- Road complexity (Road_Score) – crossings, junctions, and traffic signals raise accident severity.
