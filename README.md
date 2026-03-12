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

Our single prediction model (machine fails or not) achieved the following F1-macro score for 3 different classifier models:
- Logistic Regression: 0.54
- XGbooster Classifier: 0.52
- Random Forests CLassificator: 0.56

So our best model predicted correctly 57 out of 68 failures, and had only 21 false positives+false negatives. This means that even though there were some misses in our model, it will address correctly most failures.
Usually, a machinery stoppage that is a predictive maintenance, takes no longer than 4h, while corrective maintenance takes over 24h many times.

That being said, without machine data monitoring: 68 failures * 24 hours --> Total of 1632 hours of machine downtime

With the presented model: 57 predicted failures + 10 false positives * 4 hours of intervention: 268 hours 11 false negatives, leading to machine failures * 24 hours: 264 hours total: 532 hours of machine downtime

Our Predictive machinery model has a potential of **reducing a total of 1100 hours of maintenance for the business, representing a total of 67% of downtime reduction**

### Multilabel Classification

Our models could not handle well RNF failure modes, as its name says, it is random, so no clear pattern could be seen. Also, our model had dificulties handling this kind of failure, so these two were not part of our final predictor.

About PWF, HDF and OSF were handled very well by our model, with the following results:
 Sum of correct predictions for RFC_Single: 52
 Sum of correct False Positives for RFC_Single: 2
 Sum of correct False Negatives for RFC_Single: 10

So our model, considering only these 3 modes of failure, not only correctly predicted a machine failure, but also directed the maintenance team 81% of the times to the root cause of the failure, even if there are more than one failure occurring at once.

The Random Forest classificator is a robust classificator, that has performed very well for predicting a machine failure, and also what kind of failures are happening.

More information can be seen in the notebooks provided

## 🛠️ Tecnologies used

All the libraries used can be seen into the requirements.txt

## ▶️ How to run the projects
All the notebooks are in the folder "Notebook", to be used via Jupyter Notebooks, and the dataset is loaded within the notebooks.
The libraries used are shown in the requirements.txt
