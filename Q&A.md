1. What is overfitting? 

Overfitting means that the model fits the sample dataset so well that it fails to generalize. Overfitting model cannot perform well with unseen datasets. When the model is trained on sample dataset for too long, or the model is too complex, it is likely to cause overfitting. Overfitting model has low bias and high variance as it gets very sensitive to small changes. Therefore, it is common to separate datasets into training and testing sets. If the model has low error rate on training set, but high error rate on testing set, it is likely to be overfitted. A common method used to detect overfitting is k-fold cross-validation. Training with more data, selecting features, applying regularization could help prevent overfitting.

Reference: https://www.ibm.com/cloud/learn/overfitting

Please briefly describe what is bias vs. variance.

Bias represents the distance between predicted values and the actual values. Variance represents the spread of the data. When a model is too simple, or under-fitted, it has high bias because its preductions are inaccurate. It has low variance because it is less likely to change. When a model is too complicted, or over-fitted, it has low bias, but high variance, meaning that the model could not generalize well to unseen data. A good model needs to balance between these two factors to have a suitable level of complexity, reaching low bias and low variance. The total error of a model is bias^2 + variance + irreducible error. 
![image](https://user-images.githubusercontent.com/76275089/177248067-b0538be5-b6fd-46df-8e15-609b2127e2c3.png)

Reference: https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229


2. How do you overcome overfitting? Please list 3-5 practical experience.   

- Cross-validation: separate data into several fold, such as 5 folds. Use 4 folds to train data and test on the remaining fold. 
- Data augmentation: if cannot increase size of dataset, transform data 
- Feature selection: only select the most important features by testing out different set of features
- L1 / L2 regularization: add a penalty term to push some coefficients to 0

Reference: https://towardsdatascience.com/8-simple-techniques-to-prevent-overfitting-4d443da2ef7d

What is 'Dimension Curse'? How to prevent?

High dimension data is hard to visualize and interpret. When dimension increases, the space gets larger so the data is sparser. This makes grouping data more difficult. With fixed number of data, as the dimension increases, the predictive power of a model first increases, then decreases. 



9. Please briefly describe the Random Forest classifier. How did it work? Any pros and cons in practical implementation?
10. Please describe the difference between GBM tree model and Random Forest.
11. What is SVM? what parameters you will need to tune during model training? How is different kernel changing the classification result?
12. Briefly rephrase PCA in your own way. How does it work? And tell some goods and bads about it.
13. Why doesn't logistic regression use R^2?
14. When will you use L1 regularization compared to L2?
15. List out at least 4 metrics you will use to evaluate model performance and tell the advantage for each of them. (F1 score, ROC curve, recall, etc…)
16. What would you do if you have > 30% missing value in an important field before building the model?
