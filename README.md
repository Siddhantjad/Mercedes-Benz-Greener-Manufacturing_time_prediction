# Mercedes-Benz-Greener-Manufacturing

![mercedes-factory](https://user-images.githubusercontent.com/90169527/155000917-97c33e54-a4a5-4ed4-8dd5-3ea2c23e9afb.jpg)


## Introduction:
Mercedes known for their automotive innovations has a wide range of cars with customizable options for their customers. Before hitting the market the car needs to undergo a series of tests like safety, reliability and robustness of the components.

### Business problem:
The business problem here is to predict the amount of time that each car with a specific set of configurations will spend on the test bench. This is a regression problem that we need to solve since the target variable is a continuous variable.
The use case for this problem is to reduce the amount of time that a car spends on a test bench undergoing various tests. This can be achieved by grouping the cars with similar features while sending them on the test bench. When we group the cars based on their configuration similarity they all undergo almost similar testing techniques which reduces the unwanted changes in the testing rig and thereby reducing the time and emissions spent on testing.

### ML formulation
The Target variable is a continuous variable and represents the time in seconds that the car took to pass testing. Also the data set comprises an anonymous set of variables which reduces the scope for feature engineering. Since the target variable ‘y’ is a continuous variable , we can formulate the problem as a Regression problem. There is no strict latency constraints , the model can return the output in few seconds to a few mins

#### Source of Data:
The data is sourced from the Kaggle competition with the link:
https://www.kaggle.com/c/mercedes-benz-greener-manufacturing/data
This dataset contains an anonymized set of variables, each representing a custom feature in a Mercedes car. For example, a variable could be 4WD, added air suspension, or a head-up display.
The ground truth is labeled ‘y’ and represents the time (in seconds) that the car took to pass testing for each variable.
Variables with letters are categorical. Variables with 0/1 are binary values.

I am choosing to use R Square here since it determines how good the best fit line and also ranges from 0 to 1
### Process Stepby step :
#### 1.The aim of the problem is to predict the testing time that a car would spend on a test bench.
  The business problem does not require any latency constraints. So we can leverage this to train complex models.
#### 2. Out of the 378 features we have only 8 categorical features and 370 binary features. This makes the data highly sparse and hints for the need of PCA.
  Categorical data needs to be encoded. Since the data is already sparse, Instead of using one hot encoding I would like to use Unicode equivalent for the string.
#### 3. There is very less scope for feature engineering here since the categories are anonymous and are also sparse.
#### 4. There are no null values in the dataset and does not need any imputation.
#### 5. We had done Univariate, Bivariate and Multivariate analysis on categorical vs Target variables and the individual binary features.
#### 6. The important features is determined the feature importance provided by the decision trees.
#### 7. Next we try to reduce the dimensions using PCA and also to maintain 95% of the explained variance. The data needs to be standardized before applying PCA.
#### 8. First will create a baseline model XGboost.
#### The performance metric used here is R square.
#### 9. Based on the output of the baseline model we can train complex models like stacking models and gradient boosted trees.
#### 10. Concluded that the RandomForest trained on Selected Features by RandomForest model is giving highest score of all Public Score: 0.55468 and Private score: 0.54815 on Kaggle

## Conclusion: 
##### the RandomForest trained on Selected Features by RandomForest model is giving highest score of all Public Score: 0.55468 and Private score: 0.54815 on Kaggle
