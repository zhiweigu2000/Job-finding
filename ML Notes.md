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

### Parametric model

Parametric model: number of paramaters is fixed

e.g Regression, Naive Bayes, Simple Neural Network

Non-parametric model: number of parameters can grow

e.g. KNN, SVM, Decision Tree


### Linear Regression

Linear regression: least square y = ax + b

<img src="https://user-images.githubusercontent.com/76275089/146848745-ccb0a104-4c3c-4df0-ac54-4b8fbe34603c.png" width = 300>

<img src="https://user-images.githubusercontent.com/76275089/146848769-4d390f4b-e9f1-4aaa-901e-43f5ea0cdb73.png" width = 300>

Find minimum: take partial derivative with respect parameters

Root Mean Squared Error(RMSE): average loss

Decrease as number of features decrease

<img src="https://user-images.githubusercontent.com/76275089/146849740-f84c0f5d-1f77-4fb3-ae49-b63ae173b1df.png" width = 300>

Multiple R^2: square of the correlation between true y and predicted y

Increase as number of features increase

<img src="https://user-images.githubusercontent.com/76275089/146849906-30d2fce1-86be-40a6-86f1-cbdc31c6c68a.png" width = 150>

<img src="https://user-images.githubusercontent.com/76275089/146849909-75dc93b9-05b5-4eb2-a58d-07ca33db84bc.png" width = 300>

Residuals are orthogonal to the span of X

<img src="https://user-images.githubusercontent.com/76275089/146850439-cb51f47b-7755-4b04-afeb-4a3f4583dfd5.png" width = 150>

Least square estimate for theta

<img src="https://user-images.githubusercontent.com/76275089/146850524-685d0ffa-bf4a-4f1d-a860-ca663288b9bb.png" width = 200>


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

Bayes theorem: P(A|B) = P(B|A)P(A) / P(B)

Calculate the probability for every factor, select the outcome with the highest probability

E: event

x1, x2, ...: test actors

Calculate P(x1|E), P(x2|E), ..., find maximum probability

Use when there is a small dataset and few features

Requires features to be independent

Suitable for categorical variables

e.g text analysis, spam

References: https://medium.com/machine-learning-101/chapter-1-supervised-learning-and-naive-bayes-classification-part-1-theory-8b9e361897d5




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

