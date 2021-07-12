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

