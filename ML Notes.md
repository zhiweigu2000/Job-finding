# ML Notes

### Bias-variance trade-off

<img src="https://user-images.githubusercontent.com/76275089/125311252-d9c99180-e365-11eb-9d45-7e33aa98670f.png" width = 500>

Bias: error between average model prediction and ground truth

Variance: error from sensitivity to small fluctuations

Low model complexity, high bias, low variance, underfitting

High model complexiy, low bias, high variance, overfitting

Model error = bias^2 + variance + random error


### Cross-validation

Avoid over-fitting

Model use k-1 fold for training, validate on remaining fold, select the best parameter


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

For classification problem b0 + b1x1 + b2x2 = ln(p)

Deal with high dimensions, strong correlation

Minimize cost function: gradient descent

Regularion: prevent overfitting, add a extra term into the cost function
![image](https://user-images.githubusercontent.com/76275089/126343104-20a3b405-53aa-43d8-830a-35a0fc425e7c.png)


### SVM

Support Vector Machine: find out a plane that differentiate two categories, maximize margin

Transform data into linear

Supporting vector: the closet training example, important for determining the plane


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


### KNN

K-Nearest Neighbor: calculate distance between query example and current example, pick first K entries, return mode of labels/average

Larger K, more stable, end when there are more errors

Disadvanatge: slower when number of examples and variables increases


## Unsupervised learning

### PCA

Principal Component Analysis: reduce number of variables

Standardization z = (value - mean) / sd

Covariance matrix calculation, calculate first several eiginvalues and euginvectors, find major components that are orthogonal

Orthogonal: most distinct, cover more information

Recast data along principle component


### K-means clustering

K-means clustering:  minimize the distance of the points in a cluster with their centroid

Select k centroids, assign points to cloest centroids, calculate new centroids until converge

