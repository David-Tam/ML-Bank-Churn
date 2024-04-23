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
First of all, let's load up the dataset:
![alt text](images/1.png)

Also, data point will be droped if there is any missing piece within a client's data. We can see that the dataset has a dimension of 9998-by-14: 9998 client data points and 14 variables. The "Exited" variable indicates if the client left the bank or not (1 means the client left).
