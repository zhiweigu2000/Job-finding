## 1. Metrics you will use to evaluate model performance and tell the advantage for each of them. (F score, ROC curve, recall, etc…)

<img width="600" alt="image" src="https://user-images.githubusercontent.com/76275089/180141538-d7556b89-9408-44b4-9991-b79f254ddc15.png">

Type I error: False positive, null hypothesis is true but rejected

e.g. Consider someone as guilt when someone is actually not

Type II error: False negative, null hypothesis is false but fails to be rejected 

e.g. Covid negative result for someone who actually has Covid, cause the spread of disease

Accuracy = TP + TN / total = number of correct predictions / total number of predictions

Precision = TP / TP + FP

Recall / Sensitivity / True positive rate = TP / TP + FN

Specificity / True negative rate = TN / TN + FP

F1 score: harmonic mean between precision and recall, high F1 score if both precision and recall are high

<img width="500" alt="image" src="https://user-images.githubusercontent.com/76275089/180140424-7fde800e-b0d9-4e94-aed4-736cdf89a3c2.png">

Reference: https://towardsdatascience.com/the-f1-score-bec2bbc38aa6


## 2. Correlation and covariance

<img width="200" alt="image" src="https://user-images.githubusercontent.com/76275089/181431850-830a3df1-5045-4102-803a-bef88d433f71.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/76275089/181432034-06e72e65-5b31-448a-8672-9d006cba0eba.png">


## 3. p-value

Measure the probability of obtaining the observed results, assuming that the null hypothesis is true

Minimum significance level at which you can reject the null hypothesis


## 4. What is overfitting? 

Overfitting means that the model fits the sample dataset so well that it fails to generalize. Overfitting model cannot perform well with unseen datasets. When the model is trained on sample dataset for too long, or the model is too complex, it is likely to cause overfitting. Overfitting model has low bias and high variance as it gets very sensitive to small changes. Therefore, it is common to separate datasets into training and testing sets. If the model has low error rate on training set, but high error rate on testing set, it is likely to be overfitted. A common method used to detect overfitting is k-fold cross-validation. Training with more data, selecting features, applying regularization could help prevent overfitting.

Reference: https://www.ibm.com/cloud/learn/overfitting

Please briefly describe what is bias vs. variance.

Bias represents the distance between predicted values and the actual values. Variance represents the spread of the data. When a model is too simple, or under-fitted, it has high bias because its preductions are inaccurate. It has low variance because it is less likely to change. When a model is too complicted, or over-fitted, it has low bias, but high variance, meaning that the model could not generalize well to unseen data. A good model needs to balance between these two factors to have a suitable level of complexity, reaching low bias and low variance. The total error of a model is bias^2 + variance + irreducible error. 
![image](https://user-images.githubusercontent.com/76275089/177248067-b0538be5-b6fd-46df-8e15-609b2127e2c3.png)

Reference: https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229

Low bias machine learning algorithms: Decision Trees, k-NN, SVM

High bias machine learning algorithms: Linear Regression, Logistic Regression

How do you overcome overfitting? Please list 3-5 practical experience.   

- Cross-validation: shuffle data randomly, separate data into several fold, such as 5 folds. Use 4 folds to train data and test on the remaining fold to retain the evaluation score
- Data augmentation: if cannot increase size of dataset, transform data 
- Feature selection: only select the most important features by testing out different set of features
- Add noise
- L1 / L2 regularization: add a penalty term to push some coefficients to 0
- Perform early stopping

Reference: https://towardsdatascience.com/8-simple-techniques-to-prevent-overfitting-4d443da2ef7d

Overcome underfitting

- Add features
- Increase time of training


## 5. What is 'Dimension Curse'? How to prevent?

High dimension data is hard to visualize and interpret. When dimension increases, the space gets larger so the data is sparser. This makes grouping data more difficult. With fixed number of data, as the dimension increases, the predictive power of a model first increases, then decreases. 


## 6. Confounding variables

Confounding variable: variable that influence both the dependent variable and the independent variable

<img width="200" alt="image" src="https://user-images.githubusercontent.com/76275089/180937210-fea572cc-f948-43ee-bb5c-d7a1d99c7cce.png">

Collider: variable that are influenced by both the dependent variable and the independent variable

<img width="200" alt="image" src="https://user-images.githubusercontent.com/76275089/180937489-46051435-b5cf-4e99-85e3-51c13c06a016.png">


## 7. ROC

True positive rate and false positive rate at different threshold

<img width="500" alt="image" src="https://user-images.githubusercontent.com/76275089/181432793-ed4d63a7-eb1f-44c0-be33-18d1f4c4b0e3.png">


## 8. Supervised learning

Supervised learning: use of labeled dataset

e.g regression, decision tree, kNN, SVM, naive bayes, neural network (in most cases)

Unsupervised learning: use of unlabeled dataset

e.g. clustering


## 9. What is SVM? what parameters you will need to tune during model training? 

SVM is support vector machine. The objective is to find a hyperplane in the space that distinctly classifies the data and maximize the margin between the data from both classes. In order to do this, a kernal function is used to help transform a lower dimension space to a better dimension. We use a loss function to make sure the actual values and the predicted values have the same sign. 

Reference: https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47

How is different kernel changing the classification result?

Kernal transform data into desirable format.

- Linear kernal: best kernel when there are lots of features, faster, used for text classification
- Polynomial kernal
- Gaussian Radial Basis Function: non-linear data
- Sigmoid Kernel: used for neural network

Reference: https://dataaspirant.com/svm-kernels/#t-1608054630720


## 10. Ensemble algorithms

Ensemble algorithms tries to improve the performance of the models by combining predictions from multiple models. Popular tree based ensemble algorithms are AdaBoost, Random Forest, and XGBoost.

For AdaBoost, it starts with using a weak model such as a decision tree. Based on the result of the decision tree, we calculate the error term and add weights to incorrect values. The final result would be the result of a majority vote for all weak models. AdaBoost only has a few hyperparameters that need to be tuned in order to achieve a good result. However, AdaBoost does not work well with too much noise and when irrelevant features are included in the model.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/76275089/182049490-1a8cf9d6-a0a9-4f1a-a97b-31bf18b3e6de.png">

For Random Forest, it draws a random sample from the dataset and a number of features, and then built a model based on the sample. The result is decided by the majority vote of the trees. Random forest is less affected by noise and it generalizes better. However, it has more hyperparameters so it requires more knowledge on the topic. 

For XGBoost, it uses a regression tree. It assigns a score to each leaf which sum up to use as the final prediction. The advantage of XGBoost is that it is much faster than other algorithms. However, XGBoost is more difficult to understand and tuned. 

Reference: https://towardsdatascience.com/the-ultimate-guide-to-adaboost-random-forests-and-xgboost-7f9327061c4f


## 11. Please briefly describe the Random Forest classifier. How did it work? Any pros and cons in practical implementation?

Random forest classifier is based on decision tree. For classification tasks, the output is the class selected by most decision trees. Random forest could fix the errors of decision trees, such as overfit. For each decision tree, it is trained on a slightly different dataset. The dataset could be generated through bootstrap with replacement or selecting different features for each model. Since decision trees are sensitive to the data, the results are different for each tree. 

Pros of random forest is that offers to a way to balance bias and variance because decision trees are easy to overfit and the random forest helps solve this problem. It is less likely to be affected by outliers. It also works well with large number of features. Cons of random forest is that it requires lots of calculation and it is hard to interpret the result. 

Reference: https://towardsdatascience.com/understanding-random-forest-58381e0602d2
https://medium.datadriveninvestor.com/random-forest-pros-and-cons-c1c42fb64f04


## 12. Please describe the difference between GBM tree model and Random Forest.

GBM is gradient boosting machines. After evaluting the first model, increase the weight for observations that are hard to predit and reduce the weight for observations that are easy to predict. So the overall model is now model 1 + model 2, and then buid the next model based on the error of the this overall model.

The main difference is that for GBM tree model, each model is built based on the previous one, while in random forests, all models are built at the same time. In gradient boosting model, each tree tries to improve the deficiencies of the previous tree, such as fitting the residue of the previous model. Gradient boosting model could get a more accurate result, but also more likely to overfit.

Reference: https://towardsdatascience.com/understanding-gradient-boosting-machines-9be756fe76ab
https://www.baeldung.com/cs/gradient-boosting-trees-vs-random-forests


## 13. Clustering

Objective: entities within a group are similar, but groups are different from each other

Homogeneity within cluster: sum of squares

Gini impurity metric: measure the homogeneity of a set of items, from 0 to 1

<img width="200" alt="image" src="https://user-images.githubusercontent.com/76275089/182051406-2e0ed1e7-4797-4848-a2c5-e00d90525266.png">


## 14. Briefly rephrase PCA in your own way. How does it work? And tell some goods and bads about it.

PCA is principal component analysis. It is a method used when there are a lot of variables, it helps reduce the dimension of feature space. First standardized the data. Using simple value decomposition, we could find out the principal components. They are actually combination of features. Principal components are orthogonal to each other so they can capture more variance.  

PCA helps reduce correlated features and prevent overfitting. The disadvantage of PCA is that it makes the data harder to interpret because it is the linear combination of multiple variables. 

Reference: https://programmathically.com/principal-components-analysis-explained-for-dummies/
https://www.i2tutorials.com/what-are-the-pros-and-cons-of-the-pca/


## 15. Why doesn't logistic regression use R^2?

R^2 equals to 1 minus the error squared divided by the total variance, which equals to the variance explained by the model divided by total variance. It has the assumption that total variance equals to the variance explained by the model plus the error variance (from the ordinary least square). This assumption no longer holds in logistics regression.

Reference: https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/
https://en.wikipedia.org/wiki/Coefficient_of_determination


## 16. When will you use L1 regularization compared to L2?

For L1 regularization, we assign a feature with a 0 weight to remove this feature. L1 model will use only a subset of features and remove features that are highly correlated. L2 regularization would make the weight of some features small, but do not equal to 0. L2 has a closed form of solution, but L1 does not. L1 regularization is more robust and create sparser output, so I would use L1 regularization when there are lots of features. 

Reference: https://neptune.ai/blog/fighting-overfitting-with-l1-or-l2-regularization#:~:text=The%20differences%20between%20L1%20and,of%20squares%20of%20the%20weights


## 17. Missing values

If there is no pattern in missing values, missing values can be substituted with mean or median values, or ignored, or set as default value. If there is a high percentage of values missing, we could probably ignore this missing value. 


## 18. Outliers

- Change it with a mean or median
- Standardize the feature, smooth the outliers
- Log transform
- Drop the values


## 19. MANOVA Assumptions

- Independent Random Sampling: observations are independent of one another, no pattern for the selection of the sample, sample is completely random
- Absence of multicollinearity: dependent variables cannot be too correlated to each other
- Normality: multivariate normality is present in the data
- Homogeneity of Variance: variance between groups is equal


## 20. Paired t-test

Null hypothesis: the difference between the paired population means is equal to 0

- The variables are independent of one another.
- The difference should be approximately normally distributed

1. Standard error = sd / sqrt(sample size)
2. t = average difference / standard error
3. df = sample size - 1, find t-value
4. t smaller than t-value, cannot reject


## 21. F-test

Null hypothesis: two populations have the same variance

- Data is normal
- Variance of each treatment group is the same
- All observations are independent

F = between group / within group


## 22. Chi-square test

Goodness of fit: decide whether a variable comes from certain distrbution

Test of independence: decide whether two variables are independent


## 23. Hierarchical model

A hierarchical model is a type of statistical model that is organized into a hierarchy of different levels or layers. Each level of the hierarchy represents a different aspect or component of the data being modeled, and the levels are connected to one another in a way that allows information to flow from one level to another.

An example of a hierarchical model is a hierarchical linear model, which is used to model data with multiple levels of grouping or nesting. For example, you might use a hierarchical linear model to analyze test scores for students in different schools, where the schools are the highest level of the hierarchy, and the students are the lowest level. The model would allow you to estimate the average test scores for each school, while also taking into account the variation in scores between students within each school.


















