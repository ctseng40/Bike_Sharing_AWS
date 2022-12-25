# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Chin-Yuan Tseng
#### E-mail: ctseng40@gatech.edu

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The output from the model only contains the predicted demand. We need to insert a column of time_stamp to the predicted demand for submission.

### What was the top ranked model that performed?
The top five ranked model for data with added features were: WeightedEnsemble_L3, LightGBMXT_BAG_L2, CatBoost_BAG_L2, ExtraTreesMSE_BAG_L2, LightGBM_BAG_L2

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
We found that the date data was in DateTime format; most models could not interpret this. Therefore, we extracted the year, month, and day from the original DateTime data and added three columns to the data. We also change the datatype of season, workday, holiday, weather, and year from numerical to categorical.

### How much better did your model preform after adding additional features and why do you think that is?
The Kaggle score is improved by 27.5% through adding more features. The features we added to the model was the year, month, and day which are very important for predicting demand at each date. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The hyperparameter I tried, e.g., eval_metric & time_limit, did not improve the kaggle score

### If you were given more time with this dataset, where do you think you would spend more time?
Trying to add more features to the model; explore the performance of more models; hyperparameter tuning (split the taining data into train/validation)

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model       |eval_metric            |time_limit|presets_score|score  |
|------------|-----------------------|----------|-------------|-------|
|initial     |root_mean_squared_error|600       |best_quality |1.79201|
|add_features|root_mean_squared_error|600       |best_quality |1.29862|
|hpo_1       |root_mean_squared_error|1200      |best_quality |1.30123|
|hpo_2       |r2                     |600       |best_quality |1.30028|


### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary
In this project, we use the "Tabular Prediction" model from AWS AutoGluon to fit regression models on "Bike Sharing Demand" data from Kaggle. There are three experiment scenarios: 1) Fit the models on original train data and evaluate the model performance on test data; 2) Extract year, month, and day data from the original "DateTime" column and add the additional column to the data for model fitting; 3) Change the "time_limit" and "eval_metric" hyperparameters. The result shows that scenario 2, i.e., adding more features to the model, was the most effective way to improve model performance on the test dataset. The performance gain is 27.5%. 
