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

![Model](https://user-images.githubusercontent.com/82052288/114435419-cd019a00-9bcc-11eb-9f02-a2b5f713c8e3.jpg)

The model with highest validation accuracy was obtained using XGBoost (from 0.63 to 0.67). However, when training the considered models, I used the datasets that include data on team statistics during the match which is not correct, since this match data reflect the result obtained. 

The prediction accuracy without team statistics data ranged from 0.56 to 0.59 (where 0.5 = randomly guessing correctly), which is slightly lower than the bookmaker's accuracy (0.57 – 0.59).
### Profit
I chose the XGBoost model as my best model for profit calculations, because it has the highest validation accuracy. 
![Profit_final](https://user-images.githubusercontent.com/82052288/114435579-fa4e4800-9bcc-11eb-846c-5ba2acfe1360.jpg)

I calculated the percentage profit by dividing the income by the cost of the investment.  It is shown that if I use statistical data it is possible to make a profit, but this is basically impossible because the data were received during the match. Without taking the data into account, you only lose 1-6% over a fairly long period (more than six months).
### Future Development
Further development is possible in two directions. 

The first direction is the search and improvement of the models (there is a difference between the accuracy of training and test data). Possible options: using team statistics from previous matches; ignoring matches at the beginning of the Championship (due to insufficient information content); setting the threshold value; using other algorithms etc.

The second direction is important for the theory and methodology of training athletes. Analysis of the influence of team performance (statistical data) on the achievement of the result.  
