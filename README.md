# ML-Bank-Churn
This is a machine learning project on kaggle that aims to predict if a bank customer is going to leave the bank or continue to be a costumer.

The description can be found in:

https://www.kaggle.com/competitions/playground-series-s4e1/overview

The datasets can be accessed in this directory, or here:

https://www.kaggle.com/datasets/shubhammeshram579/bank-customer-churn-prediction/data

The project will be presented in the following structure:

**1. Data Access**

**2. Data Visualization**
   
**3. Data Preparation**
   
**4. XGB Classifier**   

**5. GBM Classifier**   

**6. ROC curves analysis**

## 1. Data Access

Let's load up the dataset. Note that a data point will be droped if there is any missing piece within a client's data.
![alt text](images/1.png)

It has a dimension of 9998-by-14: 9998 client data points and 14 variables.

## 2. Data Visualization
Info of each variable can be accessed through pie charts. But let's have a look on how much clients left the bank.

The "Exited" variable indicates if the client left the bank or not:
![alt text](images/2a.png)

Now let's see all categorical and continuous variables in the dataset.

### a) Categorical Variables
A for-loop is used to visualize all categorical variables.
![alt text](images/2b.png)

Gender classification of clients:
![alt text](images/Gender.png)

Number of years the customers with the bank:
![alt text](images/Tenure.png)

Number of bank products clients using:
![alt text](images/NumOfProducts.png)

Do the clients have credit card (0 means no)?
![alt text](images/HasCrCard.png)

Where are the clients?
![alt text](images/Geography.png)

Are the clients active (0 means no)?
![alt text](images/IsActiveMember.png)


### b) Continuous Variables
Similarly, a for-loop is used to visualize all continuous variables. Distribution of each client type (excited or not) will be shown in each continuous variable.
![alt text](images/2c.png)

The credit score distributions:
![alt text](images/CreditScore.png)

Age distribution:
![alt text](images/Age.png)

How are their account balance?
![alt text](images/Balance.png)

Their salary?
![alt text](images/EstimatedSalary.png)

### c) Correlation matrix
Now let's see the correlation matrix for all relevant variables. Irrelevant variables: 'RowNumber', 'CustomerID', 'Surname', 'Geography' are removed from the dataset.
![alt text](images/2d.png)

The corresponding heat map:
![alt text](images/corr_heatmap.png)

## 3. Data Preparation
In this project, 90% of the data is used for training and 10% for testing. Of course, our response variable is 'Exited' as we want to prediction if a client is staying (or not):
![alt text](images/3.png)

For each categorical variable, dummy variables are created for each type within the categorical variable.

## 4. XGB Classifier
First we used XGB classifier to model and make prediction. Here are the key settings:
1. Logistic regression is used for the classification work.
2. Gamma = 1 and subsample = 0.9 to allow a flexible/complex model. The depth = 5 and reg_lambda = 10 to prevent overfitting.
3. Scale_pos_weight = 5 since it is expected that more than 80% of clients stay (else the bank has a SEROUS problem).
4. Only half features are used to train each tree.
5. Since it is a binary classification. Evaluation metric is set to be AUC. The training will stop when no improvement in 10 rounds.
![alt text](images/4a.png)
![alt text](images/4b.png)

Lets make some predictions and validate! It is easy to see the model's quality with a confusion matrix. True and predicted label indicate the distributions in reality and model prediction.
![alt text](images/4c.png)
![alt text](images/CM_xgb.png)

Of course, we would like to see what feature affect most. The model indicates age, number of bank products (1~3) and active member status affect a client decision most.
![alt text](images/4d.png)
![alt text](images/FI_xgb.png)

Also, if the values within a feature are shuffled, how are their importance change? This permutation importance plot shows that the age and number of bank products (1~2) are important features (same as before).
![alt text](images/4e.png)
![alt text](images/PI_xgb.png)


## 5. GBM Classifier
The key settings of GBM classifier are basically the same as the LGB one, but it is worth to mention that not only auc, but log loss and mean accuracy are also used to evaluate.
![alt text](images/5a.png)
![alt text](images/5b.png)

Now let's see the confusion matrix:
![alt text](images/5c.png)
![alt text](images/CM_gbm.png)

The feature importance:
![alt text](images/5d.png)
![alt text](images/FI_gbm.png)

And the permutation importance:
![alt text](images/5e.png)
![alt text](images/PI_gbm.png)

## 6. ROC analysis
Let's compare the models' quality. An useful tool to see a classifier’s performance is the ROC curve. The ROC curve indicates how the true positive (TP) rate (sensitivity) and false positive (FP) rate (1- specificity) change by varying the probability threshold in a classifier.

Each point at the curve contains TP and FP rate at a threshold. A perfect classifier would have the TP rate
= 1, and the FP rate = 0, where a perfectly random classifier would have a diagonal line as a ROC curve.
In principle, if the TP and FP rate are known at a given threshold, all matrix elements in confusion matrix can be
calculated. Essentially, the ROC curve captures all confusion matrices for all thresholds.

It seems that both classifiers have almost same quality for this classification project, but LGB classifier may have a slightly better result:
![alt text](images/6.png)
![alt text](images/ROC.png)
