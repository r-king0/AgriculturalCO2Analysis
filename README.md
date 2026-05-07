# Regression of Agricultural Data
A regression project analyzing CO2 emissions using the [Agri-food CO2 emission dataset]([https://www.example.com](https://www.kaggle.com/datasets/alessandrolobello/agri-food-co2-emission-dataset-forecasting-ml/data)). The goals are:
1. Train models to predict the temperature change per year given data features - as of currently, I'm comparing and contrasting the results of a linear regression model vs a random forest regressor using the RMSE and $R^2$. Gradient boosting, dedicated time-series methods e.g. ARIMA, and deep learning models are not included, but will likely be considered in a future update.
2. Identify the most predictive features and sources of carbon emissions.

The data is separated into a training and test set using a time series split (trained on pre-2014 data and tested on post-2014), and then fed through a pipeline which processes and feature scales the data. The processed datasets are used to train and test the learning models.
## Key Results
Our RMSE and $R^2$ scores for the regression models are:

| Score   | Linear Regression| Random Forests Regression|
|-------- | ---------------- | -------------------------|
|  RMSE   | 0.423            |  0.572                   |
| $R^2$   | 0.251            |   -0.37                  |

In summary, the linear regression model has a much stronger predictive utility than the random forest regression model (RFR). In fact, RFR performs far worse than predicting just the mean. The reason for this was because of the usage of time series splitting, where early data may not take into account the accelerating rate of global warming and under-predicts recent temperature changes which have larger values than earlier ones (see plots below). In particular, the inability of RFR to extrapolate makes it is especially bad at forecasting. That said, the linear regression model can only explain $\sim25\%$ of the variance and is likely not sufficient to accurately predict temperature changes as it is. Possible ways to improve performance of the models could including adding the mean latitude and longitude of each area as additional features, as well as taking into account existing greenhouse gas in the atmosphere. 

<img width="789" height="390" alt="image" src="https://github.com/user-attachments/assets/5fb779d6-82c6-457c-8a18-458457e0a535" />

<img width="790" height="390" alt="image" src="https://github.com/user-attachments/assets/6cf3668f-7e57-472d-8212-b5281d9e1c17" />

The most important features in terms of predicting the temperature change are the year (which is likely reflective of current greenhouse gas emissions) and the geographic Area. Food retail was determined to be the most important emission sources in terms of determining the temperature change.

<img width="744" height="455" alt="most_predictive_features" src="https://github.com/user-attachments/assets/33b68fb4-ca90-47ed-9242-b9c6a46aa4bf" />

<img width="769" height="455" alt="image" src="https://github.com/user-attachments/assets/087e0cbf-a99c-4d52-b6ce-4c9fa60856ce" />

