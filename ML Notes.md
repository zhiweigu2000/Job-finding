# ML Notes

#### Bias-variance trade-off
![image](https://user-images.githubusercontent.com/76275089/125311252-d9c99180-e365-11eb-9d45-7e33aa98670f.png)

Bias: error between average model prediction and ground truth

Variance: error from sensitivity to small fluctuations

Low model complexity, high bias, low variance, underfitting

High model complexiy, low bias, high variance, overfitting

Model error = bias^2 + variance + random error


#### Cross-validation

Avoid over-fitting

Model use k-1 fold for training, validate on remaining fold


## Supervised learning

#### Parametric model

Parametric model: number of paramaters is fixed

e.g Regression, Naive Bayes, Simple Neural Network

Non-parametric model: number of parameters can grow

e.g. KNN, SVM, Decision Tree


#### Regression

Linear regression: least square y = ax + b

Logistic regression: for classification problem b0 + b1x1 + b2x2 = ln(p)

Deal with high dimensions, strong correlation

Minimize cost function: gradient descent

Regularion: prevent overfitting, add a extra term into the cost function
![image](https://user-images.githubusercontent.com/76275089/126343104-20a3b405-53aa-43d8-830a-35a0fc425e7c.png)


#### SVM

Support Vector Machine: find out a plane that differentiate two categories, maximize margin

Transform data into linear

Supporting vector: the closet training example, important for determining the plane


#### Decision tree

Decision tree: divide based on different properties

Deal with non-linear cases


#### KNN

K-Nearest Neighbor: calculate distance between query example and current example, pick first K entries, return mode of labels/average

Larger K, more stable, end when there are more errors

Disadvanatge: slower when number of examples and variables increases


## Unsupervised learning

#### PCA

Principal Component Analysis: reduce number of variables

Standardization z = (value - mean) / sd

Covariance matrix calculation, calculate first several eiginvalues and euginvectors, find major components that are orthogonal

Orthogonal: most distinct, cover more information

Recast data along principle component


#### K-means clustering

K-means clustering:  minimize the distance of the points in a cluster with their centroid

Select k centroids, assign points to cloest centroids, calculate new centroids until converge

