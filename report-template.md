# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Miyoko Shimura 28.05.2023

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

The problem was mostly about building the environment.
I had error when trying to submit my predictions to Kaggle using my API.
I looked for mentors help platform and found that I had to install Kaggle
using !pip install kaggle. Additionally, I had to to specify that autobluon
should be the version 0.6.2. to avoid errors.

### What was the top ranked model that performed?
Based on the provided leaderboard, the best performing model is the "WeightedEnsemble_L3" model.
It has the highest "score_val" of -52.559299.
which indicates better performance compared to other models on the validation data. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?

-There are more demands of bycicles in sunny days and less in rainy days 
-The demand is decreasing in the summer between 2011-2012
-Humidity is left skewed and Windspeed is right skewed
-Temp, Atemp, are normally distributed

### How much better did your model preform after adding additional features and why do you think that is?
Adding new features, such as day, year, hour, and define categorical value can improve the model
accuracy. Thus, Treating categorical features correctly can improve the model's ability.
This improvement led to drop the score from 1.749 to 0.69476.

This is thanks to proper handling of categorical features.
By explicitly specifying the data type as "category", 
AutoGluon understands that these features represent discrete categories rather than numerical values.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Although there was a slight fluctuation after adjusting hyporparametors,
model's overall performance improved with each iteration.
ASdjustments made to the hyperparameters and feature engineering is basically beneficial.

Model score  : [52.56, 30.17, 37.04]
Kaggle score : [1.75, 0.69, 0.47]

### If you were given more time with this dataset, where do you think you would spend more time?
With additional time, I would take time for EDA to check the correlation between features.
For example, considering the correlation between humidity and bicycle demand would be insightful.  


### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|timelimit|presets|method|score|
|--|--|--|--|--|
|initial|600|best_quality|none|1.74997|
|add_features|600|best_quality|regression|0.69476|
|hpo|600|best_quality|tabular_autogluon|0.47101|


### Create a line plot showing the top model score for the three (or more) training runs during the project.

[model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

[model_test_score.png](img/model_test_score.png)

## Summary
Although I have tried such EDA using Tableau and Excel, I felt EDA process in Python
is more difficult since ML algorithms such as AutoGluon originally sees all the features as ints.
But usually, many of collected data is represented as categories. This analysis is good start to
create more projects using Cloud ML platforms. I gained 
