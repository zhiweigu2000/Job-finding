## 1. Why is bias used in NN?

Bias term is a constant value that shifts the output. 
Bias allows the activation function to shift left or right, enabling the neural network to model relationships more effectively. 

## 2. What is backpropagation?

The backpropagation algorithm looks for the minimum value of the error function in weight space using a technique called delta rule or gradient descent.

- Forward pass: neuron processes the data by applying weights, biases, and activation functions, output is compared to the actual, calculate loss
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/0cbbc6d3-653c-4238-89b8-7623f3500a8b">
  
- Backward pass: calculates the gradient of the loss function with respect to each weight and bias
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/b19f095a-5bdc-46c6-882b-97ede0688282">
  
- Gradient descent: use the gradient to update the weights and biases in the direction that minimizes the error.
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/76398743-4fa9-4bcb-9b85-8b7beca6fb45">

## 3. What is vanishing gradient?

If the activation functions (like Sigmoid or Tanh) squash their inputs to very small ranges, the gradients (derivatives) often become smaller and smaller with each layer.

The gradient will be vanishingly small, effectively preventing the weight from changing its value. In worst case, this may completely stop the neural network from further training.

Common solutions:

1. Use other activation functions such as ReLU.
2. Use residual networks.
3. Use batch normalization.

## 4. What it exploding gradient

The large error gradients accumulate and result in very large updates to neural network model weights during training. 

This may make the model unstable and unable to learn from the data.

Common solutions:

1. Gradient clipping: if the gradients exceed a certain threshold, rescaled
2. L2 regularization on weights
3. Change the error derivative before back propagating it

## 5. Can we initialize weights with 0?

This causes every neuron to behave the same during training since they receive the same gradient, making it impossible for the network to learn.

## 6. Compare logistic regression and neural network

We can think of logistic regression as a one layer neural network.

Logistic regression is more interpretable.

NN fit data better than logistic regression because the complicated structure of MLP make neural network able to extract useful features, also more prone to overfitting.

## 7. How to perform hyperparameter tuning?

- Grid Search: search through a manually specified subset of the hyperparameter space, evaluates all combinations of specified hyperparameter values.

- Random Search: randomly samples combinations of hyperparameters from specified distributions, doesn't evaluate all combinations.

## 8. How to prevent overfitting?

- Data Augmentation: introduce variations to the training data to make the model more robust, such as rotations, flips, scaling, adding noise to image data.

- Use dropout layer: randomly drops a fraction of neurons during training.
  
- Regularization

- Early stopping: stop training when the model’s performance on a validation set starts to degrade.

- Cross-validation

- Batch normalization: normalizes activations in the network

## 9. What is dropout?

During training, it randomly sets a fraction p of the neurons to zero at each training step. This means that they do not contribute to the forward pass (the output) and do not participate in backpropagation (the gradient updates).

Not needed during testing

- Reduce overfitting
- Promote Redundancy

## 10. What is batch normalization?

Standardizes the inputs to a layer for each mini-batch. This has the effect of stabilizing the learning process and dramatically reducing the number of the training epochs.

During training, the mean and variance are calculated based on the specific batch while they are calculated based on all the batches during testing phase.

- Accelerate training
- Improve stability
- Reduce overfitting

## 11. Why is non linear activation function needed?

- Produce a nonlinear decision boundary via nonlinear combinations of the weights and inputs.

- Capture complex pattern, build hierarchical representations of data

## 12. Compare common activation functions 

<img width="800" alt="image" src="https://github.com/user-attachments/assets/05011b52-2da7-4204-9cc3-cabe151db44c">

**Sigmoid**

Range: 0 to 1

Advantages:
- Suitable for binary classification tasks in the output layer because output is between 0 and 1.
- Its derivative is easy to compute, which simplifies backpropagation.

Disadvantages:
- Vanishing Gradient Problem: for very high or very low inputs, the gradient becomes very small, slowing down learning and making it hard for the network to learn effectively.
- Outputs are not zero-centered, gradients can consistently push in one direction.

**Tanh**

Range: -1 to 1

Advantages:
- Outputs are zero-centered, which can help with convergence during training as gradients can be positive or negative.
- Generally performs better than sigmoid in practice, especially for hidden layers, as the output is normalized.

Disadvantages:
- Suffer from the vanishing gradient problem, less severe than sigmoid.

**ReLU**

Range: 0 to inifinite

Advantages:

- Computationally efficient, easy to compute, allowing for faster training.
- Help mitigate the vanishing gradient problem, as the gradient is constant (1) for positive values.
- Encourages sparsity in activations as many outputs are zero, which can lead to better feature learning.

Disadvantages:

- Dying ReLU Problem: Neurons can become inactive and stop learning if they output zero consistently (i.e., for negative inputs), use Leaky ReLU
- Outputs are not zero-centered, which can affect convergence

**Leaky ReLU**

<img width="500" alt="image" src="https://github.com/user-attachments/assets/2cd81e2e-ebab-47cc-a83a-95db75fd9d16">

Range: negative infinite to infinite

Advantages:

- Addresses the dying ReLU problem by allowing a small, non-zero gradient for negative inputs, enabling the model to continue learning.
- Maintains many of the benefits of ReLU in terms of computational efficiency and convergence.




