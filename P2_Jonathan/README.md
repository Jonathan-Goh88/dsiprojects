### Introduction

The goal of this project would be to predict price of houses for sale using a model developed based on the Ames Housing Data set by identifying the main features that influence the prices of these houses. The Ames Housing Dataset is a detailed and robust dataset comparing over 70 different featured relating to houses. This project aims to create a price prediction model based on the datasets provided to predict the price of houses for sale.

___

### Overview

The relevant python libraries and data were imported into the jupyter notebook file to start. The dataset underwent thorough cleaning, exploration and engineering to be made suitable for model fitting. Linear Regression, Ridge, Lasso and Elastic Net modeling will be attempted to select a best performing model that can then be used to predict the price of houses. Performance of the final model will be benchmarked against other models on Kaggle.

To refer to Data Documentation file for Metadata.

___

#### Data Cleaning, Exploration, Engineering and Visualization

Trend investigation revealed multiple columns with null or zero values. MS SubClass should be nominal as it is simply a category of the housing type. Ordinal features required encoding, null values needed to be filled, erroneous cells had to be corrected and outliers required dropping. Features with a large number of null or similar values were dropped. Identifiers were dropped. Features given as year were changed to age.

Heatmaps as well as several histograms, scatterplots barplots and boxplots were plotted to identify collinearity, as well as, features that had same or largely similar values which were then further dropped. Dummy variables were then created for the categorical features.

The test dataset was put through the same transformations that the train dataset had undergone. It was further found that the test dataset had some features that did not exist in the train dataset and vice versa. Extra features that did not exist in the train dataset were dropped while additonal columns filled with zeros were added to the the test dataset for features that were missing.

___

#### Modeling

The transformed train was underwent a train test split. The data from the split was then used to used to create linear regression, Ridge and Lasso models which were then cross-validated. The initial Lasso model was found to reduce the number of features to 79. These 79 features were then modeled again using Ridge, Lasso and Elastic Net. The Lasso model gave the best performance of the 3 but no further reduction in features was observed based on the coefficients. The 3 models agreed on what would be the top 30 coefficients albeit with some minor variations in order. 

These top 30 coefficients were then used to train the initially transformed train dataset which was then used to predict the housing prices of the test dataset. The predictions were then uploaded to Kaggle for scoring.

___

#### Conclusions and recommendations

On the whole, the quality and size of the house had the biggest weightage on the price of the house. Factors such as age had a negative impact. Being located in some neighborhoods could lead to a positive or negative impact on the price. The demographics of the housing market differ from city to city but features such as size, quality, condition and the neighborhood the house is located in can generally be applied to any house world-wide. To make a comparable model, we can start with these features and their corresponding price/valuations before going on further to identify the other additional factors.