# Viet Nam Stock Market Prediction - 5th place

This repository contains code used to achieve 5th place in the Viet Nam Stock Market Prediction
Kaggle 02 - TowardDataScience on Kaggle (https://www.kaggle.com/c/stock-market-prediction/overview)


## Models

In this competition, I first started with XGBoost model for regression and pick out only 3 features (symbols, month, and day of year). Becuase I joined the competition quite late when I just had 5 days for submissions. On the last day, I decided to do weighted average ensemble with 11 different models. Because the big idea of ensembling is that if we have a collection of individually imperfect (and independent) models, the "one-off" mistakes made by each model are probably not going to be made by the rest of the models, and thus the mistakes will be discarded when averaging the models. 

- Below is the model summary with some adjustments in ensembling weights which is different from the weights I used.

|        Model                  |    MAPE (5-fold CV)                   |  Public score  | Private score   | Ensembling weight |           
|-------------------------------|---------------------------------------|----------------|-----------------|-------------------|
| XGBRegressor                  | 0.013                                 | 4.775          | 5.323           | 5                 |      
| BaggingRegressor              | 0.015                                 | 4.727          | 5.336           | 2                 | 
| RandomForestRegressor         | 0.0150                                | 4.730          | 5.339           | 2                 |  
| LinearRegression              | 0.112                                 | 13.827         | 13.640          | 1                 |         
| TweedieRegressor              | 0.105                                 | 12.260         | 12.301          | 1                 | 
| AdaBoostRegressor             | 0.016                                 | 4.784          | 5.340           | 2                 | 
| MLPRegressor                  | 0.040                                 | 7.747          | 8.264           | 1                 |         
| GradientBoostingRegressor     | 0.014                                 | 4.745          | 5.286           | 3                 | 
| StackingRegressor             | 0.290                                 | 41.913         | 41.46           | 1                 |                  
| ExtraTreesRegressor           | 0.013                                 | 4.790          | 5.327           | 3                 |     
| HistGradientBoostingRegressor | 0.015                                 | 4.445          | 4.926           | 7                 |      



## After weighted average ensemble

|  Public score  |  Private score  |
-----------------|-----------------|
| 4.253          | 4.587           |
