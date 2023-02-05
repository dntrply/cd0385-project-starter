# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Piyush Mehta

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Negative results are not accepted. Any negative results need to be set to 0 (zero) prior to submission

### What was the top ranked model that performed?
WeightedEnsemble_L3 was the top ranked model

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The exploratory analysis indicated that one or more parts of the date - such as hour - could be used to add an additional feature
Furthermore, certain values that appear numeric, are in fact categorical - so changing the data types of the "season" and "weather" features may prove helpful.

### How much better did your model perform after adding additional features and why do you think that is?
The model performed significantly better after the addition of additional features and categorization. Adding the hour additional feature likely allowed the model to improve the hourly predictions. Adding the categorization likely helped with identifying the right model and the right tuning parameters.

## Hyper parameter tuning
### How much better did your model perform after trying different hyper parameters?
The model again performed yet better with hyper parameter tuning. The kaggle submission score improved.

### If you were given more time with this dataset, where do you think you would spend more time?
Spend more time with the hyper parameter tuning and investigate various regression models. There likely is further room for improvement.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.

model	       | hpo1	                               | hpo2	          | hpo3	                                                             | score
initial      | eval_metric=root_mean_squared_error | time_limit=600 | presets='best_quality'                                             | 1.78336
add_features | eval_metric=root_mean_squared_error | time_limit=600	| presets='best_quality'                                             | 0.63048
hpo	         | eval_metric=root_mean_squared_error | time_limit=600	| hyperparameter_tune_kwargs:num_trials = 5:search_strategy = 'auto' | 0.48260	

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![image](https://user-images.githubusercontent.com/17679107/216824941-235f8fae-ad91-4ac1-b29f-f6f3e373e8e6.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![image](https://user-images.githubusercontent.com/17679107/216824994-971ebe53-4062-4dce-bdfa-81540a2e0453.png)

## Summary

A AutoGluon model with hyper parameter optimization proved to be one with the best Kaggle score. Hyper parameter tuning or optimization allows the user to discover a model that performs better.

We started off with the simplest option where we made little or no change to the data and specified just a few basic parameters specified, such as the evaluation metric (eval_metric='root_mean_squared_error') and presets (presets='best_quality'). This gave us a quick sense of the workflow and a baseline model score.

We performed an EDA (Exploratory Data Analysis) on the data. We started by plotting the histogram. We chose to use the hour part of the date. We also realized and opted to set certain feature (season and weather) as categorical (and not have the model treat them as literal int values)

Based on adding and categorizing the features, the model showed a substantial improvement.

Lastly, we ventured into the more complex hyper tuning parameters using hyperparameters and hyperparameter_tune_kwargs. We used the approach outlined at # from https://auto.gluon.ai/stable/tutorials/tabular_prediction/tabular-indepth.html. We determined that the Kaggle submission score further improved with this set of hyper parameter tuning.

Further hyper parameter tuning is likely to improve the models. The Kaggle submission score will likely improve with the improvement in the models.
