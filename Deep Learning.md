## Convolutional Neural Network CNN 

Best suited for spatial data like images

e.g. ResNet, VGG, Efficient Net

Input layer

Convolutional layer: perform convolution operations by sliding learnable filters (kernels) over the input to detect features such as edges, textures, or more complex structures

Max pooling layer: reduce the spatial dimensions (height and width) of the feature maps by summarizing sub-regions, take the maximum value in each window

Fully Connected Layer: combine extracted features and perform the final classification, apply non-linear activation functions e.g. ReLu

Dropout layer: randomly dropping out (setting to zero) a fraction of the neurons during training, prevent overfitting

Output Layer: softmax for classification

## Recurrent Neural Network RNN

Best suited for sequencial data like text

Input layer: batch size for number of sequences processed at once, time steps for length of the sequence

Recurrent layer: each time step in the sequence one at a time, while maintaining a hidden state that captures the context of previous time steps

Dropout layer

Fully Connected layer

Output layer

### Long Short-Term Memory LSTM

An improved version of RNN

Vanilla RNNs struggle to learn from long sequences because they tend to forget information after many time steps due to vanishing gradient problem

LSTM introduces the concept of memory cells and gates (input, forget, and output gates) that allow it to explicitly control what information is kept, updated, or forgotten

Selectively chooses what it remembers

Selectively decides to forget

Selects how much of it’s memory to output

- Cell state: a memory unit that can carry information across many time steps
- Hidden state: the hidden state is updated at each time step, but it interacts with the cell state via gates
- Input gate: controls how much of the new input to store in the cell state
- Forget gate: decides which part of the cell state to forget
- Output gate: determines how much of the current cell state to pass to the next hidden state and the output

### Gated Recurrent Unit GRU

Simpler than the standard LSTM

- Merge the cell state and hidden state
- Reset gate: determines how much of the previous hidden state to forget
- Update gate: combines the forget and input gates, controls how much of the previous hidden state to keep and how much of the current input to pass to the next hidden state

## Transformer

Attention mechanism allows the model to focus on different parts of the input sequence when generating each element of the output sequence, instead of relying solely on the hidden state passed through each time step

Attention assigns weights to different parts of the input data

Transformer processes the entire sequence in parallel, using self-attention to figure out which parts of the sequence are important in relation to each other

Self-attention mechanism computes the relationships between different positions in a single sequence by using query, key, and value vectors

### BERT

A pre-trained language model that uses the encoder part of the Transformer to capture bidirectional context, meaning it looks at both the left and right contexts of a word in a sentence during training

BERT processes a sentence in both directions simultaneously

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

<img width="800" alt="image" src="https://github.com/user-attachments/assets/0b1a0175-51a8-49f9-a6a0-728f3852bf07">

<img width="800" alt="image" src="https://github.com/user-attachments/assets/929de84a-46a4-490b-bd57-ac0f198bf09f">

## 13. Compare common optimizers 

<img width="800" alt="image" src="https://github.com/user-attachments/assets/05311312-cb75-40ff-9c08-eab02205dbe5">

SGD: update the model parameters based on the gradient of the loss function calculated from a small subset (mini-batch) of the training data.

Momentum: build up velocity in the relevant direction by considering past gradients, thus smoothing out the updates and speeding up convergence.

Adagrad: adapt the learning rate for each parameter individually based on the historical gradient information. It increases the learning rate for infrequent parameters and decreases it for frequent parameters.

RMSprop: use a moving average of squared gradients to scale the learning rate.

Adam: combines the advantages of RMSprop and Momentum by maintaining a moving average of both the gradients and their squared values.

## 14. Impact of batch size

Smaller batch sizes lead to more frequent updates, introducing noise that can help the model escape local minima and potentially improve generalization, though they may result in longer training times. 

Conversely, larger batch sizes provide smoother and more stable gradient estimates, allowing for faster convergence in terms of epochs, but they can increase the risk of overfitting and require more memory. 

## 15. Impact of learning rate

A high learning rate can accelerate convergence, allowing the model to learn quickly, but it risks overshooting the optimal solution, leading to divergence or instability. 

Conversely, a low learning rate ensures more stable and precise updates but can result in excessively slow convergence, potentially getting stuck in local minima. Additionally, an inappropriate learning rate can lead to poor generalization, as it may cause the model to either underfit or overfit the training data. 

## 16. Problem of Plateau

A plateau refers to a flat region in the loss landscape where the gradients are very small or zero.

When a model encounters a plateau, the training process can slow down significantly.

Strategies:
- Adaptive learning rates
- Momentum methods
- Adaptive Optimizers

## 17. Problem of saddle point

A saddle point is a point in the loss landscape where the gradient is zero, but it is not a local minimum. In a saddle point, the surface curves upwards in some directions and downwards in others.

Difficult for the optimizer to find the optimal path.

Strategies:
- Stochasticity, introduce noise in the training process
- Momentum methods
- Adaptive Optimizers

## 18. When will transfer learning make sense?

- Limited data availability
- Similar tasks
- High computational cost
- Improve generalization














