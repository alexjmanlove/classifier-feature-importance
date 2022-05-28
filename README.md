# Ethics 2: Coursework 1 - Team 7

## Overview
The idea of this notebook is to explore ways to evaluate the significance of predictors/features in a binary classification problem.

To do this, we take inspiration from Shapley values and consider how the ROC curve / Area Under Curve changes with the addition/removal of a given predictor X_i.

✔ Pros:
* This method is model agnostic.
* This method is fairly easy to interpret.

❌ Cons:
* This method involves computing one model for each element in the powerset of predictors. This has computational complexity O(2^p), where p is the number of predictors. Therefore it is not recommended to perform this analysis for a large number of predictors.


# Figures
## Figure 5 - Pairs Plot of Generated Data 
![image](https://user-images.githubusercontent.com/79708390/170829876-2c11cbea-6b3b-4b30-9a2d-6bcc6d5b00bc.png)

## Figure 6 - Visualisation of AUC Estimation by 10-Fold Cross Validation for Nested SVM Classifiers.
![image](https://user-images.githubusercontent.com/79708390/170829934-002e90f0-3bb2-4071-8b54-85399a63774d.png)

## Figure 7 - Boxplot of AUC Distributions and Estimate of Contribution of Each Predictor (95% CI)
![image](https://user-images.githubusercontent.com/79708390/170829881-dc946e4d-ad3e-44c4-a78a-f2d5fda961f3.png)
![image](https://user-images.githubusercontent.com/79708390/170829887-a62f6651-8681-4760-b6f9-cfa62ed25d42.png)

## Figure 3 - SHAP Estimate of Feature Importance
![image](https://user-images.githubusercontent.com/79708390/170829900-b6e002f3-e92f-46c3-815d-892812e398e2.png)

## Figure 4 - In-built ensemble.RandomForestClassifier() feature importance. 
![image](https://user-images.githubusercontent.com/79708390/170830035-4572c105-f64c-44ad-af8e-52f26666d397.png)
