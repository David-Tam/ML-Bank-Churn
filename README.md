# ML-Bank-Churn
This is a machine learning project on kaggle that aims to predict if a bank customer is going to leave the bank or continue to be a costumer.

The description can be found in:

https://www.kaggle.com/competitions/playground-series-s4e1/overview

The datasets can be accessed here:

https://www.kaggle.com/datasets/shubhammeshram579/bank-customer-churn-prediction/data

The project will be presented in the following structure:

**1. Data Access**

**2. Data Visualization**
   
**3. Data Preparation**
   
**4. XGB Classifier**   

**5. GBM Classifier**   

**6. ROC curves analysis**

## 1. Data Access
First of all, let's load up the dataset. Note that a data point will be droped if there is any missing piece within a client's data.
![alt text](images/1.png)

It has a dimension of 9998-by-14: 9998 client data points and 14 variables.

## 2. Data Visualization
Info of each variable can be accessed through pir charts.

The "Exited" variable indicates if the client left the bank or not:
![alt text](images/2a.png)

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
Similarly, a for-loop is used to visualize all continuous variables.
![alt text](images/2c.png)


Four variables: 'RowNumber', 'CustomerID', 'Surname', 'Geography' are removed from the dataset before trainning as they are irrelevant variables.
![alt text](images/2d.png)
