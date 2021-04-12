# Prediction of Number of Goals in Football

#### Build models and determine the accuracy (profit) of the model predicting the number of goals scored (under or over 2.5) in a football match in three top Championships of England, Italy and Spain.
### Introduction and Aim
Result is the most important thing in sports. In football, goals are a means of achieving results and goals scored are one of the most important tasks in a match.

Firstly, prediction is of great importance for the betting business allowing it to predict various aspects of sports events.
Secondly, prediction is used to identify areas for improving the training of athletes and teams.

Using the teams’ data analysis, a model that can predict the number of goals scored in a match was built. Based on the such models, one can test their assumptions / hypotheses and use it as an example / basis for other models.
#### Technologies Used
*Python*

*Pandas*

*Numpy*

*Scikit-Learn*

*XGBoost*
### Data
The data on the last three seasons plus the current one (2020/2021) for the three most popular European Championships - English, Spanish and Italian, was taken from the website (http://football-data.co.uk/).
### Preprocessing
At the first stage of the data analysis, three events containing NaN were found and deleted (the code is shown only with deletion, it is located before training the models).

At the second stage, a function that creates standings that are updated after each match was built. Also, the indicators that characterize the ability to score and concede for each team were calculated in the standings. There were built functions to select the required indicators and a function that adds ranks of team; points of team; indicators on goals scored and conceded before the match.

At the third stage, a function that prepared the dataset for training using the previously described functions was applied to each dataset.
### Modelling
Three seasons (1140 samples) will be used to build the model, and the model will be validated for the current season for each Championship separately (274-290 samples depending on the Championship). All matches up to March 31 2021 were selected for validation. The data with 30 features and a set of 18 features without team statistics during the match (for the most accurate model) was used.

I did another data split into Train and Validation data in preparation for using GridSearch Cross Validation. I also chose 5-fold cross validation.

For the majority of models I created, I applied hyperparameter tuning, where I started with a broad range of hyperparameters, and tuned for optimal train accuracy and validation accuracy.
