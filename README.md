# A SHAP-Inspired Method for Feature Importance

## Overview

The idea behind this notebook is to explore a concept that came to me while studying SHAP values. 
The aim is to evaluate the significance of predictors/features in a binary classification problem.

To do this, we take inspiration from SHAP and consider how a given model evaluation metric changes with the addition/removal of each predictor X_i. In this way we can seek to quantify the contribution of X_i to the model metric. In this example we will consider AUC as the metric of interest, however Precision, Recall and other metrics are equally viable.

✔ Pros:
* This method is model agnostic.
* This method can be used to estimate any desirable metric of interest.
* This method is fairly easy to interpret.

❌ Cons:
* This method involves computing one model for each element in the powerset of predictors. This has computational complexity O(2^p), where p is the number of predictors. Therefore it is not recommended to perform this analysis for a large number of predictors.


# Figures

## Figure 1 - EDA Visualisation of Generated Data
This figure contains pairwise plots of the generated data. The data contain 1000 observations of four predictors X_1,...,X_4. From these scatterplots and KD estimates we observe 𝑋2 demonstrates minimal separability, while 𝑋3 demonstrates the greatest separability.
![image](https://user-images.githubusercontent.com/79708390/170829876-2c11cbea-6b3b-4b30-9a2d-6bcc6d5b00bc.png)

## Figure 2 - Visualisation of AUC Estimation by 10-Fold Cross Validation for Nested SVM Classifiers.
For each classifier we have plotted ten ROC curves as a dashed line over 200 thresholds, corresponding to the 10-folds. The mean of the 10-folds is plotted as a solid line with shaded areas denoting confidence intervals at the 95% level.
![image](https://user-images.githubusercontent.com/79708390/170829934-002e90f0-3bb2-4071-8b54-85399a63774d.png)

## Figure 3 - Boxplot of AUC Distributions and Estimate of Contribution of Each Predictor (95% CI)
In the left-hand plot, we see that predictors 𝑋1, 𝑋3 and 𝑋4 are associated to higher AUCs when included in a model. By contrast, the quantiles of partitioned samples corresponding to 𝑋2 show no significant difference. The right-hand plot containing the estimates for Gain in mean AUC suggests that the inclusion of 𝑋2 corresponds to a negligible change in classifier performance overall. These point estimates xi_i are shown with confidence intervals corresponding to the 95% level, with standard error as a function of the sample variances for the AUCs, s_{M_i}^2, s_{M_-i}^2,
![image](https://user-images.githubusercontent.com/79708390/170830341-a18df9ae-f032-4d38-9d3e-09908385a987.png)
![image](https://user-images.githubusercontent.com/79708390/170829881-dc946e4d-ad3e-44c4-a78a-f2d5fda961f3.png)
![image](https://user-images.githubusercontent.com/79708390/170829887-a62f6651-8681-4760-b6f9-cfa62ed25d42.png)

## Figure 4 - SHAP Estimate of Feature Importance for Random Forest Model trained on all predictors.
The SHAP estimates suggest 𝑋3 is the most important feature, while 𝑋2 is the least.
![image](https://user-images.githubusercontent.com/79708390/170829900-b6e002f3-e92f-46c3-815d-892812e398e2.png)

## Figure 5 – Feature Importance Ranked by Mean Decrease in Node Impurity.
The same Random Forest model trained on all predictors also suggests 𝑋3 is the most important feature, while 𝑋2 is the least.

![image](https://user-images.githubusercontent.com/79708390/170830035-4572c105-f64c-44ad-af8e-52f26666d397.png)
