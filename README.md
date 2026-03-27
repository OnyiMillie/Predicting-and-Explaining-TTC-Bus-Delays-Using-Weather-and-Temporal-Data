Overview

Urban transit delays disrupt daily mobility and system efficiency. This project applies data analytics and machine learning to predict and explain bus delay patterns in Toronto using TTC delay data combined with historical weather data.

The objective is twofold:

Predict total daily delays across the city
Classify delay severity levels (Low, Moderate, High)
Identify high-risk routes and contributing factors


Data Sources
TTC Bus Delay Dataset https://open.toronto.ca/dataset/ttc-bus-delay-data/ 
Historical Weather Data https://climate.weather.gc.ca/climate_data/daily_data_e.html?hlyRange=2002-06-04%7C2026-03-12&dlyRange=2002-06-04%7C2026-03-12&mlyRange=2003-07-01%7C2006-12-01&climate_id=6158355&Prov=ON&urlExtension=_e.html&searchType=stnProx&optLimit=yearRange&Month=12&Day=12&StartYear=2014&EndYear=2024&Year=2025&selRowPerPage=100&Line=3&txtRadius=25&optProxType=city&selCity=43%7C39%7C79%7C23%7CToronto&selPark=&txtCentralLatDeg=&txtCentralLatMin=0&txtCentralLatSec=0&txtCentralLongDeg=&txtCentralLongMin=0&txtCentralLongSec=0&txtLatDecDeg=&txtLongDecDeg=&timeframe=2 
https://climate.weather.gc.ca/climate_data/daily_data_e.html?hlyRange=2002-06-04%7C2026-03-12&dlyRange=2002-06-04%7C2026-03-12&mlyRange=2003-07-01%7C2006-12-01&climate_id=6158355&Prov=ON&urlExtension=_e.html&searchType=stnProx&optLimit=yearRange&StartYear=2014&EndYear=2024&selRowPerPage=100&Line=3&txtRadius=25&optProxType=city&selCity=43%7C39%7C79%7C23%7CToronto&selPark=&txtCentralLatDeg=&txtCentralLatMin=0&txtCentralLatSec=0&txtCentralLongDeg=&txtCentralLongMin=0&txtCentralLongSec=0&txtLatDecDeg=&txtLongDecDeg=&timeframe=2&Day=12&Year=2024&Month=12#
https://climate.weather.gc.ca/climate_data/daily_data_e.html?hlyRange=2002-06-04%7C2026-03-12&dlyRange=2002-06-04%7C2026-03-12&mlyRange=2003-07-01%7C2006-12-01&climate_id=6158355&Prov=ON&urlExtension=_e.html&searchType=stnProx&optLimit=yearRange&StartYear=2014&EndYear=2024&selRowPerPage=100&Line=3&txtRadius=25&optProxType=city&selCity=43%7C39%7C79%7C23%7CToronto&selPark=&txtCentralLatDeg=&txtCentralLatMin=0&txtCentralLatSec=0&txtCentralLongDeg=&txtCentralLongMin=0&txtCentralLongSec=0&txtLatDecDeg=&txtLongDecDeg=&timeframe=2&Day=12&Year=2023&Month=12#

Methodology
Data Preparation
Merged multi-source datasets on temporal keys
Handled missing values and removed duplicates
Dropped non-informative features (e.g., raw Date, Time, Station)
Feature Engineering including
Temporal features: day-of-week indicators
Lag features: Lag_1 (previous day delays)
Rolling averages: Rolling_7
Interaction terms: Temp × Precipitation
Polynomial terms: Temp², Precip²
Day-of-week dummy variables

Modeling Approach
Defined two predictive tasks:
Regression: Predict total daily transit delays
Classification: Categorize delay severity (Low, Moderate, High)


Split the dataset into training and testing sets (80/20 split) to evaluate model performance on unseen data

Removed non-predictive and non-numeric features (e.g., Date, Time, Station) to ensure compatibility with machine learning models

Applied MinMax scaling after train-test split by fitting the scaler on the training data and transforming both training and test sets to prevent data leakage

Trained models on the training dataset and generated predictions on the test dataset

Implemented models:
Regression: Linear Regression
Classification: Logistic Regression, Decision Tree, Random Forest
Evaluated model performance using:
Regression: RMSE, R²

Classification: Accuracy, Precision, Recall, F1-score, Confusion Matrix
Compared model outputs to identify the best-performing model for each task


Conclusion
The models showed reasonable predictive performance, with regression results aligning moderately well with actual delays
Weather conditions (especially precipitation and snow) were key drivers of transit delays
Temporal patterns influenced delay behavior, with noticeable differences across days
Classification models were able to identify delay severity levels, though with some limitations
Overall, transit delays are influenced by multiple interacting factors, and while predictable to an extent, some variability remains unexplained
