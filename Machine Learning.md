# ML Notes

## Bias-variance trade-off

<img src="https://user-images.githubusercontent.com/76275089/147712553-7d7fce85-2a18-46ea-94f6-d4e353bab39f.png" width = 500>

Bias: error between average model prediction and ground truth

Variance: the extent to which model prediction error changes based on inputs, error from sensitivity to small fluctuations

Low model complexity, high bias, low variance, underfitting

High model complexiy, low bias, high variance, overfitting

Model error = bias^2 + model variance + random error (observation variance)


## Regularization

Overfitting:

Model performs well with training data -- low bias

Model fails to perform well with testing data -- high variance

Underfitting:

Model accuracy is bad with training and testing data -- high bias, high variance

Prevent overfitting, add a extra term into the cost function

<img src="https://user-images.githubusercontent.com/76275089/147713522-703517f0-1b7b-4de4-af87-c2a71a20012b.png" width = 500>

L2 (Ridge) regularization: square value of a coefficient

<img src="https://user-images.githubusercontent.com/76275089/147713569-2dfaa3da-d0bf-4d56-b497-2e1ef537eac1.png" width = 400>

Always exist unique optimal parameter

L1 (LASSO) regularization: absolute value of a coefficient

<img src="https://user-images.githubusercontent.com/76275089/147713624-79ccb5ae-f211-4239-a72e-d7991b12fca8.png" width = 400>

Used for feature selection, shrink coefficients to 0


## Gradient descent

Optimize loss function

Take small steps in the direction of steepest descent for a particular object function

<img src="https://user-images.githubusercontent.com/76275089/147714298-bd9d1783-7753-4900-9c37-0eef4a6ae3e1.png" width = 300>

alpha: learning rate, too large fails to converge, too small takes too long to converge

L: loss function

Stochastic Gradient Descent: draw a simple random sample of data indices

<img src="https://user-images.githubusercontent.com/76275089/147714719-7bbf8e69-2dc8-4a87-9722-71046724b309.png" width = 400>

<img src="https://user-images.githubusercontent.com/76275089/147715065-7dd48c99-9819-4722-b64d-67853dbbca77.png" width = 500>

<img src="https://user-images.githubusercontent.com/76275089/147715069-7e8dfb72-5cf7-4aac-8297-148f942c7fe3.png" width = 500>


## Cross-validation

Avoid over-fitting

Model use k-1 fold for training, validate on remaining fold, select the best parameter

<img src="https://user-images.githubusercontent.com/76275089/147712755-319487e1-0da2-464a-8e41-606341926a2f.png" width = 500>


## Imblanced dataset

Model is only able to learn a class (e.g. always predict the dominate class) and it gets stuck in a suboptimal solution

An accuracy of over 90% can be misleading because the model may not have predictive power on the rare class

### Resampling

Oversampling

SMOTE

Downsampling

### Model-level methods

Update loss function

Tree-based models work well on tasks involving small and imbalanced datasets

Logistic regression is able to handle class imbalanced relatively well in a standalone manner. Adjust the probability threshold to improve the accuracy for predicting the minority class

### Evaluation Metrics

Use unsampled data instead of resampled data to evaluate the model

Accuracy is misleading when classes are imbalanced

AUC of the ROC curve: tune thresholds to increase recall and decrease false positive rate

Precision-Recall curve: identify a threshold that works best for the dataset, gives more importance to the positive class


## Model choice

Text data: Naive Bayes, neural network BERT

Regression: linear regression, regression tree

Classification: logistics regression, random forest, SVM

![image](https://github.com/zhiweigu2000/Job-finding/assets/76275089/2519a31c-0129-42e7-8d72-3936908b3c1c)


## Linear Regression

Linear regression: y = ax + b

Root Mean Squared Error(RMSE): how far apart the predicted values are from the observed values in a dataset

The lower the RMSE, the better a model fits a dataset

$RMSE = \sqrt{\frac{1}{n} \displaystyle\sum_{i=1}^{n}{(y_i- \hat{y_i})^2}}$

$R^2$: the proportion of the variance in the response variable of a regression model that can be explained by the predictor variables

The higher the R2 value, the better a model fits a dataset

$TSS = \displaystyle\sum{(y_i - \bar{y})^2}$

$RSS = \displaystyle\sum{(y_i - \hat{y_i})^2}$

$RegSS = TSS-RSS = \displaystyle\sum{(\bar{y} - \hat{y_i})^2}$

$R^2 = 1 - \frac{RSS}{TSS} = \frac{RegSS}{TSS}$

Residual $e_i = y_i - \hat{y_i}$

Least square estimate for theta $\hat{\theta} = (X^{T}X)^{-1}X^{T}Y$

1. What Are the Basic Assumption?

There are four assumptions associated with a linear regression model:

- Linearity: The relationship between X and the mean of Y is linear.

- Homoscedasticity: The variance of residual is the same for any value of X.

- Independence: Observations are independent of each other. Multicollinearity could cause coefficients to flip sign. Test with VIF

- Normality: For any fixed value of X, Y is normally distributed. If data is not normal, apply transformation. Test with QQ plot

2. Advantages

- Linear regression performs exceptionally well for linearly separable data

- Easy to implement and train the model

- It can handle overfitting using dimensionlity reduction techniques and cross validation and regularization

3. Disadvantages

- Sometimes lot of feature engineering is required

- If the independent features are correlated it may affect performance

- It is often quite prone to noise and overfitting

4. Whether Feature Scaling is required?

Yes, to reach the minimum quickly

5. Impact of Missing Values?

It is sensitive to missing values

6. Impact of outliers?

Linear regression needs the relationship between the independent and dependent variables to be linear. It is also important to check for outliers since linear regression is sensitive to outlier effects.

7. Types of Problems it can solve

- House Price Prediction
  
- Flight Price Prediction


## Logistic Regression

$h_{\theta}(x) = \theta_0 + \theta_1x_1 + ... + \theta_nx_n = \theta^Tx = g(\theta_0 + \theta_1x_1 + ... + \theta_nx_n)$

Let $z = \theta_0 + \theta_1x_1 + ... + \theta_nx_n$

$h_{\theta}(x) = g(z) = \frac{1}{1 + e^{-z}}$

Sigmoid: $h_{\theta}(x) = \frac{1}{1 + e^{-(\theta_0 + \theta_1x_1 + ... + \theta_nx_n)}}$

Cost function from linear regression = $\frac{1}{2} (h_{\theta}(x^i) - y_i)^2$

Squared loss: loss surface not convex (many local minimums), does not penalize wrong answers strongly

Cost function for logistics = $-ylog(h_{\theta}(x^i)) - (1-y)log(1-h_{\theta}(x^i))$

Cross-entropy loss: not get stuck, no local minimum

Performance matrix

<img src="https://user-images.githubusercontent.com/76275089/147810818-becf29cf-f804-4395-ba21-6d7b34c8b1c5.png" width = 400>

Accuracy = $\frac{TP+TN}{TP+FP+TN+FN}$

Precision = $\frac{TP}{TP+FP}$

Recall = $\frac{TP}{TP+FN}$

F1 score = $\frac{2\*Precision\*Recall}{Precision+Recall}$

Higher threshold, fewer false positive, higher precision

Lower threshold, fewer false negative, higher recall

Optimal curve: area under curve (AUC) = 1

<img src="https://user-images.githubusercontent.com/76275089/147811644-214ae1ec-d6e9-42d3-93a2-1eb15f7c7a44.png" width = 500>

Linear separability: a set of d-dimentional points is linearly separable if we can draw a degree d-1 hyperplane that separates the points perfectly

1. What Are the Basic Assumption?

Linear Relation between independent features and the log odds

2. Advantages

- Logistic regression are very easy to understand

- It requires less training

- Good accuracy for many simple data sets and it performs well when the dataset is linearly separable.

- It makes no assumptions about distributions of classes in feature space.

- Logistic regression is less inclined to over-fitting but it can overfit in high dimensional datasets. One may consider Regularization (L1 and L2) techniques to avoid over-fittingin these scenarios.

- Logistic regression is easier to implement, interpret, and very efficient to train.

3. Disadvantages

- Sometimes lot of feature engineering is required

- If the independent features are correlated it may affect performance

- It is often quite prone to noise and overfitting

- If the number of observations is lesser than the number of features, logistic regression should not be used, otherwise, it may lead to overfitting

- Non-linear problems can’t be solved with logistic regression because it has a linear decision surface. Linearly separable data is rarely found in real-world scenarios.

- It is tough to obtain complex relationships using logistic regression. More powerful and compact algorithms such as Neural Networks can easily outperform this algorithm.

- Logistic regression needs independent variables are linearly related to the log odds (log(p/(1-p)).

4. Whether Feature Scaling is required?

Yes

5. Missing Values

Sensitive to missing values

6. Impact of outliers?

Sensitive to the unusual observations: outliers, high leverage, and influential observations

7. Types of Problems it can solve (Supervised)

Classification


## SVM

Support Vector Machine: find out a plane that differentiate two categories, maximize margin

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/6005375d-a7fb-4876-a618-1c3381c5ad93" width = 400>

Supporting vector: the closet training example, important for determining the plane

Margin: separation of line to the closest class data points, good margin needs to be as far as possible for both sides

$y = w^Tx + b$

$w^Tx_1 + b = 1$

$w^Tx_2 + b = -1$

$w^T(x_2 - x_1)= 2$

$\frac{w^T}{||w||}(x_2 - x_1)= \frac{2}{||w||}$

Optimize function $max \frac{2}{||w||}$ to find two marginal plane that have the maximum distance

$min \frac{||w||}{2} + c_i \sum{n}{i=1}{e_i}$ to include some errors

Kernel: transform data into higher dimensional space

Linear problem: linear kernal

Nonlinear problem: RBF

1. What Are the Basic Assumption?

There are no such assumptions

2. Advantages
   
- SVM is more effective in high dimensional spaces

- SVM is relatively memory efficient

- SVM’s are very good when we have no idea on the data

- Works well with even unstructured and semi structured data like text, images and trees

- The kernel trick is real strength of SVM. With an appropriate kernel function, we can solve any complex problem

- SVM models have generalization in practice, the risk of over-fitting is less in SVM

3. Disadvantages

- More training time is required for larger dataset, do not work well for large dataset

- It is difficult to choose a good kernel function

- The SVM hyper parameters are cost and gamma. It is not that easy to fine-tune these hyper-parameters

- It is hard to interprete

4. Whether Feature Scaling is required?

Yes

5. Impact of Missing Values?

Although SVMs are an attractive option when constructing a classifier, SVMs do not easily accommodate missing covariate information. Similar to other prediction and classification methods, attention to missing data when constructing an SVM can impact the accuracy and utility of the resulting classifier.

6. Types of Problems it can solve(Supervised)

- Classification

- Regression

7. Overfitting And Underfitting

In SVM, to avoid overfitting, we choose a Soft Margin, instead of a Hard one i.e. we let some data points enter our margin intentionally (but we still penalize it) so that our classifier don't overfit on our training sample

8. Performance Metrics

Classification: confusion Matrix, precision, recall, F1 score

Regression: R2, Adjusted R2, MSE, RMSE, MAE


## Navie Bayes

Bayes theorem: $P(A|B) = \frac{P(B|A)P(A)}{P(B)}$

Calculate the probability for every factor, select the outcome with the highest probability

y: event

$x_1$, $x_2$, ...: test actors, given

$P(y|x_1, x_2, .., x_n) = \frac{P(x_1|y) P(x_2|y)  ... P(y)}{P(x_1) P(x_2) ... P(x_n)}$

$= \frac{P(y)\displaystyle\prod_{i=1}^{n}{P(x_i|y)}}{P(x_1) P(x_2) ... P(x_n)}$

$P(y|x_1, x_2, .., x_n) \propto P(y)\displaystyle\prod_{i=1}^{n}{P(x_i|y)}$

Select the result with maximum probability

$\hat{y} = argmax_{y_i} P(Y = y_i)\displaystyle\prod_{i=1}^{n}{P(x_i|Y = y_i)}$

e.g text analysis

Classify sentences as good or bad: remove stop words, stemming, bag of words / TFIDF, calculate the probability to classify

1. What Are the Basic Assumption?

Each $X_i$ is independent of any other $_j$X given Y

Features are given the same weight

2. Advantages

- Work very well with many number of features: treat features as independent, curse-of-dimensionality problems do not apply

- Works well with small dataset

- It converges faster when we are training the model: based on probability

- It also performs well with categorical features

3. Disadvantages

- Correlated features affects performance, which is impossible in the real life

- Zero frequency issue

4. Whether Feature Scaling is required?

No

5. Impact of Missing Values?

Naive Bayes can handle missing data. Attributes are handled separately by the algorithm at both model construction time and prediction time. As such, if a data instance has a missing value for an attribute, it can be ignored while preparing the model, and ignored when a probability is calculated for a class value.

6. Impact of outliers?

It is usually robust to outliers

7. Different Problem statement you can solve using Naive Baye's

- Sentiment Analysis

- Spam classification

- Twitter sentiment analysis

- Document categorization


## Decision tree

Decision tree: divide based on different properties

Classification or regression

All data starts in the root node

Pick the best feature and best split value

Split data into two nodes

Repeat until every node is pure or unsplittable (has duplicate data that could not be split)

Purity: entropy, Gini impurity

Entropy:

$H(s) = -p_+ log_2 (p_+) - p_- log_2 (p_-)$

$p_+$: probability of yes

Between 0 to 1, when entropy = 0, the node is pure split

Gini impurity:

$GI = 1 - \displaystyle\sum_{i=1}^{n}{p^2}$

$= 1-\[(p_+)^2 + (p_-)^2 \]$

Which feature to split: information gain

$Gain(s, f_1) = H(s) - \displaystyle\sum_{v} \frac{|s_v|}{|s|}H(s_v)$

Compare the gain the two features, choose the feature with higher gain

Decision square regressor: MSE

$MSE = \frac{1}{2m} \displaystyle\sum_{i=1}^{n}{(y_i- \hat{y_i})^2}$

Hyperparameters: max_depth, max_leaf

Avoid overfitting: don't allow fully grown tree

Set more specific rules to prevent growth

Cut off less useful branches

1. What Are the Basic Assumption?

There are no such assumptions

2. Advantages

- Clear visualization: The algorithm is simple to understand, interpret and visualize as the idea is mostly used in our daily lives. 

- Simple and easy to understand: Decision Tree looks like simple if-else statements which are very easy to understand.

- Decision Tree can be used for both classification and regression problems.

- Decision Tree can handle both continuous and categorical variables.

- No feature scaling required: No feature scaling (standardization and normalization) required in case of Decision Tree as it uses rule based approach instead of distance calculation.

- Handles non-linear parameters efficiently: Non linear parameters don't affect the performance of a Decision Tree unlike curve based algorithms. So, if there is high non-linearity between the independent variables, Decision Trees may outperform as compared to other curve based algorithms.

- Decision Tree can automatically handle missing values.

- Decision Tree is usually robust to outliers and can handle them automatically.

- Less Training Period: Training period is less as compared to Random Forest because it generates only one tree unlike forest of trees in the Random Forest

3. Disadvantages

- Overfitting: This is the main problem of the Decision Tree. It generally leads to overfitting of the data which ultimately leads to wrong predictions. In order to fit the data (even noisy data), it keeps generating new nodes and ultimately the tree becomes too complex to interpret. In this way, it loses its generalization capabilities. It performs very well on the trained data but starts making a lot of mistakes on the unseen data.

- High variance: Decision Tree generally leads to the overfitting of data. Due to the overfitting, there are very high chances of high variance in the output which leads to many errors in the final estimation and shows high inaccuracy in the results. In order to achieve zero bias (overfitting), it leads to high variance.

- Unstable: Adding a new data point can lead to re-generation of the overall tree and all nodes need to be recalculated and recreated.

- Not suitable for large datasets: If data size is large, then one single tree may grow complex and lead to overfitting. So in this case, we should use Random Forest instead of a single Decision Tree.

4. Whether Feature Scaling is required?

No

5. Impact of outliers?

It is not sensitive to outliers. Since, extreme values or outliers, never cause much reduction in RSS, they are never involved in split. Hence, tree based methods are insensitive to outliers.

6. Types of Problems it can solve

- Classification

- Regression


## Random Forest

Use a sample of data and features at each split to build decision tree

ach node is most common predictions from each model

A kind of bagging

Prevent overfitting of decision tree

Reduce high variance to low variance: with majority voting

1. What Are the Basic Assumption?

There are no such assumptions

2. Advantages

- Doesn't Overfit

- Less parameter tuning required

- Decision Tree can handle both continuous and categorical variables.

- No feature scaling required: uses Decision Tree internally

- Suitable for any kind of ML problems

3. Disadvantages

- Biased With features having many categories

- Biased in multiclass classification problems towards more frequent classes.

4. Whether Feature Scaling is required?

No

5. Impact of outliers?

Robust to outliers

6. Types of Problems it can solve (Supervised)

- Classification

- Regression


## Adaboost 

Combine weak classifier algorithm to form strong classifier based on decision stumps (trees with one node and two leaves)

1. Assign equal weight to each training item

Sum of weight = 1

2. Select feature for decision stump based on information gain / entropy / Gini

3. Total error = weight of error items

Performance of stump = $\frac{1}{2} ln(\frac{1-TE}{TE})$

4. Update the weight after the classifier the trained, reduce the weight of correct records

Correct records: new weight = old weight * $e^{-performance}$

Correct records: new weight = old weight * $e^{performance}$

Normalize new weights

5. Create random number between 0-1 to select records based on weights, create new dataset, repeat 1-4

1. What Are the Basic Assumption?

There are no such assumptions

2. Advantages

- Doesn't Overfit

- It has few parameters to tune

3. Whether Feature Scaling is required?

No

4. Missing Values

Can handle mising values

5. Impact of outliers?

Sensitive to outliers

6. Types of Problems it can solve(Supervised)

- Classification

- Regression


## Xgboost 

Extreme gradient boosting

1. Create a binary decision tree using the feature based on the residual (baseline-actual)

2. Calculate similarity weight = $\frac{\displaystyle\sum{residuals^2}}{\displaystyle\sum{p(1-p) +\lambda}}$ for each node

3. Information gain = similarity weight of nodes - similarity weight of root to select feature
  
New record: $\sigma\[average + \alpha_1(DT_1) + \alpha_2(DT_2) + ... \]$

1. What Are the Basic Assumption?

There are no such assumptions

2. Advantages

- It has a great performance

- It can solve complex non linear functions

- It is better in solve any kind of ML usecases.

3. Disadvantages

- It requires some amount of parameter tuning

4. Whether Feature Scaling is required?

No

5. Missing Values

Cannot handle missing values

6. Impact of outliers?

Robust to Outliers

7. Types of Problems it can solve(Supervised)

- Classification

- Regression

### Ensemble Techniques

Use multiple algorithms to solve a problem

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/53e628e1-b387-4373-ad59-b7e7c3801ed7" width = 400>


## KNN

K-Nearest Neighbor: calculate distance between query example and current example, pick first K entries, return mode of labels/average

Larger K, more stable, end when there are more errors

Disadvanatge: slower when number of examples and variables increases


## Unsupervised learning

### PCA

Principal Component Analysis: reduce number of variables

Simple value decomposition: X = UΣ * V^T

Principal component: UΣ column

Orthogonal: most distinct, cover more information

Recast data along principle component


### K-means clustering

K-means clustering:  minimize the distance of the points in a cluster with their centroid

1. Initialize k centroids

2. Assign points to cloest centroids

3. Compute average of each group to update centroids

4. Assign points again

Elbow method: within cluster sum of square (WCSS)

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/030d6186-19bf-49c4-8ca0-92ee26b484d0" width = 400>

Validation: Silhouette 

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/6488328e-d0c5-439a-a399-6746a2a388fb" width = 300>

a(i): sum of distance to centroid within cluster

b(i): average distance of points in one cluster to points in the other cluster

Good clustering: b(i) >> a(i)


### Hierarchical clustering

Create Dendrogram

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/c952e92b-2787-4876-ac02-23d2e9957341" width = 400>

Find the longest horizontal line that has no vertical line passed through it

Create a straight line across that line, number of intersections = number of clusters

Large dataste: k-means

Small dataset: hierarchical


### DBScan clustering

<img src="https://github.com/zhiweigu2000/Job-finding/assets/76275089/4ff68036-6443-43be-817a-02980fb41241" width = 400>

Leave outliers (noise) out of clusters


## Reference

1. https://www.youtube.com/@krishnaik06








