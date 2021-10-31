### Introduction

The Acea Group is one of the leading Italian multiutility operators that manages and develops water and electricity networks and environmental services. Its water services supply a total of 9 million inhabitants in Lazio, Tuscany, Umbria, Molise and Campania regions of Italy.
Water supply companies struggle with the forecasting of water levels in the various waterbodies they manage (water spring, lake, river, or aquifer) to handle daily consumption.

An aquifer is an underground layer of water-bearing permeable rock, rock fractures or unconsolidated materials (gravel, sand, or silt). 
___

### Overview

A dataset containing rainfall, temperature, volume drawn, hydrometry and depths at various locations linked to the Auser Aquifer was provided.
This waterbody consists of two subsystems, split into north and south, where the former partly influences the behavior of the latter. The levels of the north subsystem are represented by the depths of the SAL, PAG, CoS and DIEC wells, while the levels of the south subsystem are represented by the depth of the LT2 well.
The features to be predicted for this project are the depths of the SAL, CoS and LT2 wells. Features like rainfall and temperature affect features like depth to groundwater and hydrometry some time after. However, it is unknown how many days, weeks or months later that these effects are observed.
This project aims to build models that can forecast the depths of the targeted variables 7 days ahead. EDA, data cleaning and feature engineering will be performed on the dataset given. Following which, time series and regression models will be tried to see which of these give the lowest RMSE.
___

#### Data Cleaning, Exploration, Visualization

Values for the features of Volume CSA & CSAL from before 2014 were all zeros. Since these features are independent variables to be used as predictors, only data from 2014 onwards will be used.
Temperature Ponte a Moriano contains 0 values from 2017 onwards indicating that the field instrument failed and wasn't replaced/repaired. This feature will be dropped.
Some 0 values and null values were observed in most of the features. 0 values are taken to be instrument failures and are thus replaced with null and subsequently filled by interpolation.
___

#### Regression Modeling

The months were extracted and cyclically encoded to be used as a feature column for regression.
A rolling mean of 7 days was used to smooth out short term fluctuation.
Time shifting was done for a range of days since the number of days after that water depths are affected by rainfall and temperatures are unknown.
After each shift, the correlation with the target variable is computed and stored.
Correlation vs. the number of days shifted is plotted to find the highest correlation.
The number of days shifted that corresponds to the highest correlation for each of the rainfall and temperature features is extracted and stored in a dictionary
The features are then shifted by the number of days that correspond to the highest correlation by iterating over each key-value pair in the dictionary
All other features are shifted by 7 days since the model is intended to be a week-ahead forecast.
Stochastic Gradient Descent Regressor was used to predict the depths for the LT2, SAL and CoS wells.
___

#### SARIMA Modeling

Since the SGD regressor applied an L1 penalty and eliminated most of the feature coefficients with the exception of month and year, an attempt to use the SARIMA model was made.
Augmented Dickey-Fuller test performed and the data requires 1 level of differencing to achieve stationarity.
ACF and PACF graphs show a steep cut-off after the 1st lag.
As such, the order for the model parameters are (1, 1, 1).
The optimal seasonal parameters were obtained as (2, 0, 2) via a Gridsearch with a period of 52 weeks (i.e. a year)
___

#### Conclusions and recommendations

Predicting the water level to be within an error margin of 25cm, 12cm and 38cm for the depths at LT2, SAL and CoS respectively represents a reasonable degree of success when compared to the original standard deviation as a baseline.
Predicting the depth at SAL had the best RMSE scores while predicting the depth at CoS fared the poorest among the regressors.
SARIMA model attempt for depth at SAL performed worse than all the regression models in terms of RMSE.
Success of the regressor model in predicting the depth at SAL shows that regression with features such as water level measurements at nearby locations, rainfall measurements, temperature measurements and metering the volume of water drawn can play a vital role in predicting water availability.
However, these same features had little importance when it came to predicting LT2.
It was also noted from the background information given in Kaggle by the competition host that the Auser waterbody is split into North and South
It is likely that the majority of the predictor variables in the dataset given were mainly from the north sector. 
Additional data collection from the south sector is required to proceed further.
All models should be retrained with newer data periodically at a suitable interval depending on the level of accuracy required by the user since the residuals generally increase the further away the predicted date is from the data it is trained on.
