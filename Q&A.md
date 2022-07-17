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


3. Please briefly describe the Random Forest classifier. How did it work? Any pros and cons in practical implementation?

Random forest classifier is based on decision tree. For classification tasks, the output is the class selected by most decision trees. Random forest could fix the errors of decision trees, such as overfit. For each decision tree, it is trained on a slightly different dataset. The dataset could be generated through bootstrap with replacement or selecting different features for each model. Since decision trees are sensitive to the data, the results are different for each tree. 
Pros of random forest is that offers to a way to balance bias and variance because decision trees are easy to overfit and the random forest helps solve this problem. It is less likely to be affected by outliers. It also works well with large number of features. Cons of random forest is that it requires lots of calculation and it is hard to interpret the result. 

Reference: https://towardsdatascience.com/understanding-random-forest-58381e0602d2
https://medium.datadriveninvestor.com/random-forest-pros-and-cons-c1c42fb64f04


4. Please describe the difference between GBM tree model and Random Forest.

GBM is gradient boosting machines. After evaluting the first model, increase the weight for observations that are hard to predit and reduce the weight for observations that are easy to predict. So the overall model is now model 1 + model 2, and then buid the next model based on the error of the this overall model.
The main difference is that for GBM tree model, each model is built based on the previous one, while in random forests, all models are built at the same time. In gradient boosting model, each tree tries to improve the deficiencies of the previous tree, such as fitting the residue of the previous model. Gradient boosting model could get a more accurate result, but also more likely to overfit.

Reference: https://towardsdatascience.com/understanding-gradient-boosting-machines-9be756fe76ab
https://www.baeldung.com/cs/gradient-boosting-trees-vs-random-forests


5. What is SVM? what parameters you will need to tune during model training? 

SVM is support vector machine. The objective is to find a hyperplane in the space that distincyly classifies the data and maximize the margin between the data from both classes. In order to do this, a kernal function is used to help transform a lower dimension space to a better dimension. We use a loss function to make sure the actual values and the predicted values have the same sign. 

Reference: https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47

How is different kernel changing the classification result?

Kernal transform data into desirable format.

- Linear kernal: best kernel when there are lots of features, faster, used for text classification
- Polynomial kernal
- Gaussian Radial Basis Function: non-linear data
- Sigmoid Kernel: used for neural network
- Gaussian Kernel

Reference: https://dataaspirant.com/svm-kernels/#t-1608054630720


6. Briefly rephrase PCA in your own way. How does it work? And tell some goods and bads about it.

PCA is principal component analysis. It is a method used when there are a lot of variables, it helps reduce the dimension of feature space. First standardized the data. Using simple value decomposition, we could find out the principal components. They are actually combination of features. Principal components are orthogonal to each other so they can capture more variance.  

PCA helps reduce correlated features and prevent overfitting. The disadvantage of PCA is that it makes the data harder to interpret because it is the linear combination of multiple variables. 

Reference: https://programmathically.com/principal-components-analysis-explained-for-dummies/
https://www.i2tutorials.com/what-are-the-pros-and-cons-of-the-pca/


7. Why doesn't logistic regression use R^2?

R^2 equals to 1 minus the explained variance divided by the total variance. It has the assumption that total variance equals to the variance explained by the model plus the error variance. This assumption no longer holds in logistics regression.

Reference: https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/



15. When will you use L1 regularization compared to L2?
16. List out at least 4 metrics you will use to evaluate model performance and tell the advantage for each of them. (F1 score, ROC curve, recall, etc…)
17. What would you do if you have > 30% missing value in an important field before building the model?
18. Best model for small set of data



