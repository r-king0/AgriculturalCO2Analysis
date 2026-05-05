# Regression of Agricultural Data
A regression related project analyzing CO2 emissions from agricultural data. The goals of the project are to:
1. Train a model to predict the temperature change per year given data features - specifically, I'm comparing and contrasting the results of a linear regression model vs a random forest regressor using the RMSE and $R^2$
2. Identify the most important features and sources of carbon emissions. 
The data is separated into a training and test set using a time series split (trained on data pre-2014 and tested on post-2014), and fed through a pipeline processes and feature scales the data and is then used to train a machine learning model.
#### Key Results

Our RMSE and $R^2$ scores for the regression models are:

| Score | Linear Regression | Random Forests Regression |
| ----- | ----------------- | ------------------------- |
| RMSE  | 0.421             | 0.569                     |
| $R^2$ | 0.258             | -0.357                    |
In a nutshell, the linear regression model has a much stronger predictive utility than the random forest regression model, though it is insufficient by itself in terms of its ability forecasting future temperature changes. Notably, the RFR model performs significantly worse than predicting just the mean and should not be used for forecasting. The reason for this was because of the time series splitting, where early data may not take into account the accelerating rate of global warming and under-predicts more recent data, which often has much larger changes in temperature (see plots below). In particular, the inability of RFR to extrapolate means that it is especially bad at forecasting new data. Possible ways to improve performance of the models could be including mean latitude and longitude of each area as well as taking into account existing greenhouse gas in the atmosphere 

The most important features are predicting the temperature change are the year (which is likely reflective of current greenhouse gas emissions) and the geographic Area. Food retail was determined to be the most important emission sources in terms of determining the temperature change.
