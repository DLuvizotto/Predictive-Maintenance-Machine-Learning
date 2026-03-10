# Predictive-Maintenance-Machine-Learning
This repository focus on data science to provide predictive maintenance insights on a machine  with synthetic data

## 🎯 Project Goal
1st goal: Define a prediction model to determine when a machine is about to fail or not considering process data, in order to provide insights for the predictive maintenance team to avoid big machinery downtime.

2nd goal: Define if the machine has failed, which kind of failure is happening: There are 5 types of failure:
OverStrain Failure (OSF);
Power Failure (PWF);
Tool Wear Failure (TWF);
Heat Dissipation Failure (HDF);
Random Noise Failure (RNF);

## 📊 Dataset
The dataset has been randomly generated, and can be found in the following URL:
https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset

It has 10k rows, with the following features:
|Feature name|Role|Type|
|-------|--------|----------|
|UID|ID|Integer|
|Product ID|ID|Categorical|
|Type|Feature|Categorical|
|Air Temperature|Feature|Continuous|
|Process Temperature|Feature|Continuous|
|Rotational Speed|Feature|Integer|
|Torque|Feature|Continuous|
|Tool Wear|Feature|Continuous|
|Machine Failure|Target|Integer|
|TWF|Target|Integer|
|OSF|Target|Integer|
|HDF|Target|Integer|
|PWF|Target|Integer|
|RNF|Target|Integer|

## 🔍 Methodology

The project began with a quick data analysis, to check if there is any missing data, which is not the case.
Then, some data visualization, mainly scatter and boxplots were used to check any correlation between the features, and any characteristic that appear within our data, specially regarding the RNF behavior, as it may be a problematic target variable for our models.

Then we started our prediction model in the first step, that was a binary classification if the machine will fail or not, without checking what was the cause.
For this, we used first a logistic regression, and then we checked which predictor was better, a XGBooster classifier or a Random Forests Classifier.
Then, when the best model was selected, we further tried to improve it by checking our feature importances, and then performed a bit of feature engineering, by simplifying some features to further increase the model performance.

Then, we started a multiclass prediction, to check if our model could also correctly predict the mode of failure. We started already with the XGBoost and RFC models, with optuna to tune the hyperparameters.

Then, with our results, we also performed a third analysis, which was a model that could correctly predict a TWF, as it was a bit problematic in our second phase of the project.

## 📈 Results
## 🛠️ Tecnologies used
## ▶️ How to run the projects
