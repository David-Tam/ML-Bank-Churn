# ML-Bank-Churn
This is a machine learning project (and a kaggle competition) that aims to build an energy prediction model; for reducing the imbalance costs due to the increasing number of prosumers.

The detail description can be found in:
https://www.kaggle.com/competitions/playground-series-s4e1/overview

The datasets can be downloaded here:
https://www.kaggle.com/datasets/shubhammeshram579/bank-customer-churn-prediction/data

In general, there are 3 sections in the code:

**1. Data preparation:**
   Data cleaning, sorting and feature engineering, followed by data splitting for training and validation.
   
**2. XGBoost approach:**
   Applying XGBoost algorithm for training and evaluation of the model.
   
**3. LightGBM approach:**
   Applying LightGBM algorithm for training and evaluation of the model.

## 1. Data preparation and feature engineering
This section aims to combine all datasets into one that can be trained by the model.

First of all, let's load up all datasets:
![alt text](images/load_data.png)
