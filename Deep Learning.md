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

## 4. Exploding gradient

The large error gradients accumulate and result in very large updates to neural network model weights during training. 

This may make the model unstable and unable to learn from the data.

Common solutions:

1. Gradient clipping: if the gradients exceed a certain threshold, rescaled
2. L2 regularization on weights
3. Change the error derivative before back propagating it


