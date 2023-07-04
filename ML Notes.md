# ML Notes

### Bias-variance trade-off

<img src="https://user-images.githubusercontent.com/76275089/147712553-7d7fce85-2a18-46ea-94f6-d4e353bab39f.png" width = 500>

Bias: error between average model prediction and ground truth

Variance: error from sensitivity to small fluctuations

Low model complexity, high bias, low variance, underfitting

High model complexiy, low bias, high variance, overfitting

Model error = bias^2 + model variance + random error (observation variance)

<img src="https://user-images.githubusercontent.com/76275089/147712539-0b5d4dd2-e315-41e3-85b6-b83e2d8c16af.png" width = 600>


### Coefficients

Correlation coefficient (r): average of the product of x and y, both in standard units

Represent strength of linear regression

<img src="https://user-images.githubusercontent.com/76275089/146848646-80cd7c48-9bbb-4ada-b79b-78aa83a08e20.png" width = 200>

Root Mean Squared Error(RMSE): average loss

Decrease as number of features decrease

<img src="https://user-images.githubusercontent.com/76275089/146849740-f84c0f5d-1f77-4fb3-ae49-b63ae173b1df.png" width = 300>

Multiple R^2: square of the correlation between true y and predicted y

Increase as number of features increase

<img src="https://user-images.githubusercontent.com/76275089/146849906-30d2fce1-86be-40a6-86f1-cbdc31c6c68a.png" width = 150>

<img src="https://user-images.githubusercontent.com/76275089/146849909-75dc93b9-05b5-4eb2-a58d-07ca33db84bc.png" width = 300>


### Feature engineering

Transform raw features into more informative features for modeling

Encode non-numeric features


### Cross-validation

Avoid over-fitting

Model use k-1 fold for training, validate on remaining fold, select the best parameter

<img src="https://user-images.githubusercontent.com/76275089/147712755-319487e1-0da2-464a-8e41-606341926a2f.png" width = 500>


### Regularization

Prevent overfitting, add a extra term into the cost function

<img src="https://user-images.githubusercontent.com/76275089/147713522-703517f0-1b7b-4de4-af87-c2a71a20012b.png" width = 500>

<img src="https://user-images.githubusercontent.com/76275089/147713540-f01286fa-9801-48d3-86ac-d5982b8f17c3.png" width = 400>

L2 (Ridge) regularization:

<img src="https://user-images.githubusercontent.com/76275089/147713569-2dfaa3da-d0bf-4d56-b497-2e1ef537eac1.png" width = 400>

Always exist unique optimal parameter

<img src="https://user-images.githubusercontent.com/76275089/147713580-d18db155-1010-434f-bb46-71b379423724.png" width = 300>

L1 (LASSO) regularization:

<img src="https://user-images.githubusercontent.com/76275089/147713624-79ccb5ae-f211-4239-a72e-d7991b12fca8.png" width = 400>


### Gradient descent

<img src="https://user-images.githubusercontent.com/76275089/147714298-bd9d1783-7753-4900-9c37-0eef4a6ae3e1.png" width = 300>

alpha: learning rate, too large fails to converge, too small takes too long to converge

L: loss function

Stochastic Gradient Descent: draw a simple random sample of data indices, compute gradient estimate

<img src="https://user-images.githubusercontent.com/76275089/147714719-7bbf8e69-2dc8-4a87-9722-71046724b309.png" width = 400>

<img src="https://user-images.githubusercontent.com/76275089/147715065-7dd48c99-9819-4722-b64d-67853dbbca77.png" width = 500>

<img src="https://user-images.githubusercontent.com/76275089/147715069-7e8dfb72-5cf7-4aac-8297-148f942c7fe3.png" width = 500>


## Supervised learning

References: https://medium.com/machine-learning-101

### Parametric model

Parametric model: number of paramaters is fixed

e.g Regression, Naive Bayes, Simple Neural Network

Non-parametric model: number of parameters can grow

e.g. KNN, SVM, Decision Tree


### Linear Regression

Linear regression: y = ax + b

Minimize \displaystyle\sum{(y_i - \hat{y_i})^2}$ with gradient descent

Convergence theorem: $y = y - \frac{dy}{dx} * \alpha$

Root Mean Squared Error(RMSE): how far apart the predicted values are from the observed values in a dataset

The lower the RMSE, the better a model fits a dataset

$RMSE = \sqrt{\frac{1}{n} \displaystyle\sum_{i=1}^{n}{(y_i- \hat{y_i})^2}}$

$R^2$: the proportion of the variance in the response variable of a regression model that can be explained by the predictor variables

The higher the R2 value, the better a model fits a dataset

$TSS = \displaystyle\sum{(y_i - \bar{y})^2}$

$RSS = \displaystyle\sum{(y_i - \hat{y_i})^2}$

$RegSS = TSS-RSS = \displaystyle\sum{(\bar{y} - \hat{y_i})^2}$

$R^2 = 1 - \frac{RSS}{TSS} = \frac{RegSS}{TSS}$

Residual: $e_i = y_i - \hat{y_i}$

Least square estimate for theta

$\hat{\theta} = (X^{T}X)^{-1}X^{T}Y$

1. What Are the Basic Assumption?(favourite)

There are four assumptions associated with a linear regression model:

- Linearity: The relationship between X and the mean of Y is linear.

- Homoscedasticity: The variance of residual is the same for any value of X.

- Independence: Observations are independent of each other.

- Normality: For any fixed value of X, Y is normally distributed, if data is not normal, apply transformation

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



### Logistic Regression

<img src="https://user-images.githubusercontent.com/76275089/147809854-4139a2e3-9f91-4fc5-af53-72e64c641e4a.png" width = 300>

Minimize cost function: gradient descent

Squared loss: loss surface not convex, does not penalize wrong answers strongly

Cross-entropy loss: not get stuck, no local minimum

<img src="https://user-images.githubusercontent.com/76275089/147810255-22889ab9-092a-4dfe-8558-edd931ffca8d.png" width = 350>

<img src="https://user-images.githubusercontent.com/76275089/147810315-29ded49b-1965-435c-9a65-f2343799bac6.png" width = 500>

<img src="https://user-images.githubusercontent.com/76275089/147810818-becf29cf-f804-4395-ba21-6d7b34c8b1c5.png" width = 400>

<img src="https://user-images.githubusercontent.com/76275089/147810863-4e90b23c-b26a-4364-a812-983efedf08d2.png" width = 800>

Higher threshold, fewer false positive, higher precision

Lower threshold, fewer false negative, higher recall

Precision recall curve

<img src="https://user-images.githubusercontent.com/76275089/147811489-11b478fd-9d27-489c-b175-316e722f9d66.png" width = 500>

Optimal curve: area under curve (AUC) = 1

ROC curve

<img src="https://user-images.githubusercontent.com/76275089/147811644-214ae1ec-d6e9-42d3-93a2-1eb15f7c7a44.png" width = 500>

Optimal curve: area under curve (AUC) = 1

Linear separability: a set of d-dimentional points is linearly separable if we can draw a degree d-1 hyperplane that separates the points perfectly

L2 regularization


### Decision tree

Decision tree: divide based on different properties

Classification or regression

All data starts in the root node

Pick the best feature and best split value

Split data into two nodes

Repeat until every node is pure or unsplittable (has duplicate data that could not be split)

Entropy:

<img src="https://user-images.githubusercontent.com/76275089/146880065-42e91b83-63b9-4e03-8458-a4f854063bbe.png" width = 150>

Low entropy means more predictable

Loss of split:

<img src="https://user-images.githubusercontent.com/76275089/146880264-12ddab88-0269-4243-b700-cd6ade7dba8d.png" width = 200>

Smaller loss, better split

Avoid overfitting: don't allow fully grown tree

Set more specific rules to prevent growth

Cut off less useful branches

Random forest: build many decision trees by bootstrap, use a sample of features at each split, each node is most common predictions from each model


### SVM

Support Vector Machine: find out a plane that differentiate two categories, maximize margin

Supporting vector: the closet training example, important for determining the plane

Kernal: transformation of data 

Parameters: kernal, regularization parameter, gamma, margin

Gamma: high gamma, only near points are considered

Margin: separation of line to the closest class data points, good margin needs to be as far as possible for both sides


### KNN

K-Nearest Neighbor: calculate distance between query example and current example, pick first K entries, return mode of labels/average

Larger K, more stable, end when there are more errors

Disadvanatge: slower when number of examples and variables increases


### Navie Bayes

Bayes theorem: $P(A|B) = \frac{P(B|A)P(A)}{P(B)}$

Calculate the probability for every factor, select the outcome with the highest probability

y: event

$x_1$, $x_2$, ...: test actors, given

$P(y|x_1, x_2, .., x_n) = \frac{P(x_1|y) P(x_2|y)  ... P(y)}{P(x_1) P(x_2) ... P(x_n)}$

$= \frac{P(y)\displaystyle\prod_{i=1}^{n}{P(x_i|y)}}{P(x_1) P(x_2) ... P(x_n)}$

$P(y|x_1, x_2, .., x_n) \propto P(y)\displaystyle\prod_{i=1}^{n}{P(x_i|y)}$

Normalize, select the result with maximum probability

e.g text analysis

Classify sentences as good or bad: remove stop words, stemming, bag of words / TFIDF, calculate the probability to classify

1. What Are the Basic Assumption?

Features are independent

2. Advantages

- Work very well with many number of features: treat features as independent, curse-of-dimensionality problems do not apply

- Works well with large training dataset, or when dataset is small compared to number of features

- It converges faster when we are training the model: based on probability

- It also performs well with categorical features

3. Disadvantages

Correlated features affects performance

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


### Adaboost classifier 

Combine weak classifier algorithm to form strong classifier e.g. based on many decision stumps (trees with one node and two leaves)

After training a classifier at any level, ada-boost assigns weight to each training item, misclassified items are assigned high weight

Update the weight after the classifier the trained

For each stump, amount of say <img src="https://user-images.githubusercontent.com/76275089/179338753-0458918c-4cc3-48b7-bbd5-1a69225ddfe9.png" width = 200>

New weight = old weight * e^(-amount of say), normalizate


## Unsupervised learning

### PCA

Principal Component Analysis: reduce number of variables

Simple value decomposition: X = UΣ * V^T

Principal component: UΣ column

Orthogonal: most distinct, cover more information

Recast data along principle component


### K-means clustering

K-means clustering:  minimize the distance of the points in a cluster with their centroid

Select k centroids, assign points to cloest centroids, calculate new centroids until converge




