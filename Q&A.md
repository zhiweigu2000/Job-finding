1. What is overfitting? / Please briefly describe what is bias vs. variance.

Overfitting means that the model fits the sample dataset so well that it fails to generalize. Overfitting model cannot perform well with unseen datasets. When the model is trained on sample dataset for too long, or the model is too complex, it is likely to cause overfitting. Overfitting model has low bias and high variance as it gets very sensitive to small changes. Therefore, it is common to separate datasets into training and testing sets. If the model has low error rate on training set, but high error rate on testing set, it is likely to be overfitted. A common method used to detect overfitting is k-fold cross-validation. Training with more data, selecting features, applying regularization could help prevent overfitting.

References: https://www.ibm.com/cloud/learn/overfitting







2. How do you overcome overfitting? Please list 3-5 practical experience.    / What is 'Dimension Curse'? How to prevent?
3. Please briefly describe the Random Forest classifier. How did it work? Any pros and cons in practical implementation?
4. Please describe the difference between GBM tree model and Random Forest.
5. What is SVM? what parameters you will need to tune during model training? How is different kernel changing the classification result?
6. Briefly rephrase PCA in your own way. How does it work? And tell some goods and bads about it.
7. Why doesn't logistic regression use R^2?
8. When will you use L1 regularization compared to L2?
9. List out at least 4 metrics you will use to evaluate model performance and tell the advantage for each of them. (F1 score, ROC curve, recall, etc…)
10. What would you do if you have > 30% missing value in an important field before building the model?