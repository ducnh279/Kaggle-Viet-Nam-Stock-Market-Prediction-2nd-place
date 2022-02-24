# Viet Nam Stock Market Prediction - 5th place

This repository contains code used to achieve 5th place in the **"Viet Nam Stock Market Prediction - TowardDataScience"** competition on Kaggle (https://www.kaggle.com/c/stock-market-prediction/leaderboard)


## I. Solution Summary
![This is the solution flowchart](https://github.com/nhduc279/Kaggle-Viet-Nam-Stock-Market-Prediction-5th-place/blob/main/images/flowchart.png)


# II. Feature Selection and Extraction
![fms](https://github.com/nhduc279/Kaggle-Viet-Nam-Stock-Market-Prediction-5th-place/blob/main/images/first_feature_permutation_importance.png)

- Initially, I extracted many features from the "date" feature in the "price_train" set, such as: **['month', "day of the year", "week of the year", "day of the month", "day of the week", "quarter']**. However, after using Feature Permutation Importance with XGBoost, I realized that some features have extremely low importance. Thus, I decided to remove some features. There were 3 features left selected, including **symbols, day of the year, and month.**

- Here, I firmly believe in feature selection from the method called **"Feature Permutation Importance"**. Because it is not "inflated" with categorical features with many unique values, like the "symbol" feature, this method does not suffer from a large degree of overfitting because it uses independent datasets while computing the weight of the importance for each feature. You can see the horizontal bar chart below, which shows the relative importance of the features.


## III. Models

In this competition, I started with the XGBoost regression model and selected only three features (symbols, month, and day of the year). Because I entered the competition late, with only five days to submit, I chose to do a weighted average ensemble with 11 distinct models on the last day. Because the big idea of ensemble learning is that if we have a collection of individually imperfect (and independent) models, the "one-off" mistakes made by each model are probably not going to be made by the rest of the models, and thus the mistakes will be discarded when averaging the models. 

- Below is the model summary with some adjustments in ensembling weights that are different from the weights I used.

|        Model                  |    MAPE (5-fold CV)                   |  Public score  | Private score   | Ensembling        |      
|-------------------------------|---------------------------------------|----------------|-----------------|-------------------|
| HistGradientBoostingRegressor | 0.015                                 | 4.445          | 4.926           | 7                 |    
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



## IV. After weighted average ensemble

|  Public score  |  Private score  |
-----------------|-----------------|
| 4.253          | 4.587           |
