# Biostat 626 Midterm 1 Problem Set

## Github URL: https://github.com/kewen-li/BIOSTAT626

## Datasets
The dataset consists of the following files:

- 'training_data.txt': Training dataset
- 'test_data.txt': Testing Dataset
- 'data_dictionary.txt': Introduction of the dataset
- 'features_info.txt': Detailed information provided for each features

## Prerequisites

- Running Environment: Rstudio
- 'test_data.txt’
- 'training_data.txt'

## Libraries

These libraries are required to install.

```R
library(readr)
library(dplyr)
library(tidyr)
library(caret)
library(randomForest)
library(Boruta)
```



## Instructions

1. To reproduce the results, open Rstudio and two Rmd files for different task. (e.g. Task1.Rmd, Task2.Rmd), and install the libraries mentioned above.
2. Just Run the code sequentially, it will perform read data, data preprocessing, feature selection, train model, convert data frame and export data file these steps.
3. Each Rmd will export one txt file under the format, binary_k5484.txt or multiclass_k5484.txt, depending on which Task you run.



## Baseline Algoritm 

### Task 1

This code trains a binary classification model using the glm method from the caret package in R. The response variable is binary and the family argument is set to "binomial" to indicate that the logistic regression model should be used.

The training data is specified as X_train and y_train, while the testing data is specified as X_test and y_test. The trainControl method is set to "none", which means no resampling method will be applied, and the model will be trained on the entire training dataset.

After training the model, the predict function is used to generate predictions on the testing data (X_test). Finally, the confusionMatrix function from the caret package is used to calculate the confusion matrix and various statistics such as accuracy, sensitivity, specificity, etc.



### Task 2

This code trains a random forest model using train function from caret package

1. Randomly select a subset of features from the dataset
2. Build a decision tree based on the all features
3. Repeat steps 1 and 2 to create multiple decision trees
4. For each observation in the test dataset, predict the target class by aggregating the predictions of all the decision trees
5. The final prediction is the class with the highest frequency among all the predictions



| Baseline Model | Task 1 | Task 2 |
| -------------- | ------ | ------ |
| Performance    | 1.00   | 0.93   |



## Final algorithm

### Task 1

Same as baseline algorithm

### Task 2

The final algorithm based on the provided code uses the Boruta algorithm to select the relevant features and then performs hyperparameter tuning on a random forest model using these selected features. The algorithm then compares the results of different models trained using varying numbers of trees and finally selects the best model based on the results. The selected model is then used to predict the outcomes on the test data and evaluated using the confusion matrix.



| Final Model | Task 1 | Task 2 |
| ----------- | ------ | ------ |
| Performance | 1.00   | 0.905  |



## Leaderboard Performance

I used the Boruta algorithm to select the relevant features from the datasets. Because it can help to reduce the dimensionality of the data and remove any redundant or irrelevant features, which can potentially improve the performance of the classifiers.

After selecting the relevant features, I used the random forest algorithm for classification and tuned the hyperparameters of the random forest algorithm using cross-validation to find the best combination of parameters that can improve the performance of the model.

To further improve the performance, I tried different values for the number of trees in the random forest, ranging from 10 to 160, and used 10-fold cross-validation to evaluate the performance of each model. I also used the resamples() function from the caret package to compare the performance of different models.

Finally, I used the best model (with ntree=100 and mtry=20) to make predictions on the test dataset and evaluated the performance of the model using the confusion matrix.

The whole process took me 5 days to complete.

| Model | Task 1 | Task 2 |
| ----- | ------ | ------ |
| 1st   | 1.00   | 0.926  |
| 2nd   | 1.00   | 0.933  |
| 3rd   | 1.00   | 0.900  |
| 4th   | 1.00   | 0.905  |



##  Comments

Since the accuracy of the model on the train data is significantly higher than the accuracy on the real data, it may be an indication of overfitting. In this case, the model is fitting too closely to the training data and is not able to generalize well to new, unseen data.

To improve the classification accuracy, I will try these pontential ways:

1. Feature engineering:   selecting or creating features that are more relevant to the problem at hand, such as performing data analysis, feature selection, or by using domain-specific knowledge.
2. Hyperparameter tuning:  tunning the hyperparameters of the random forest model  to find the optimal values that result in better accuracy.
3. Model selection: It is also possible that the random forest model is not the best model for the given problem. Other models, such as gradient boosting or neural networks, could be explored to achieve better accuracy.