# Ethics 2: Coursework 1 - Team 7

## Overview
The idea of this notebook is to explore ways to evaluate the significance of predictors/features in a binary classification problem.

To do this, we take inspiration from Shapley values and consider how the ROC curve / Area Under Curve changes with the addition/removal of a given predictor X_i.

✔ Pros:
* This method is model agnostic.
* This method is fairly easy to interpret.

❌ Cons:
* This method involves computing one model for each element in the powerset of predictors. This has computational complexity O(2^p), where p is the number of predictors. Therefore it is not recommended to perform this analysis for a large number of predictors.
