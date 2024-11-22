

## 1. Fundamentals of Backpropagation

- **Forward Pass to Compute Output**
  - The forward pass involves passing input data through the network layers to compute the final output.
  - Each neuron applies a weighted sum of its inputs followed by an activation function.
  - Outputs are calculated layer-by-layer until the network produces predictions for the given input.

- **Backward Pass to Calculate Gradients Using the Chain Rule**
  - The backward pass calculates the gradients of the loss function with respect to each weight and bias in the network.
  - Gradients are computed layer-by-layer in reverse order, starting from the output layer back to the input layer.
  - The **chain rule** of calculus is applied to propagate errors backward through the network:
    - Compute the derivative of the loss with respect to the output of each neuron.
    - Use these derivatives to compute the gradients for weights and biases.
  - Handles inter-layer dependencies efficiently, ensuring correct updates for all parameters.

- **Weight Updates Based on Computed Gradients**
  - After gradients are calculated, the weights and biases are updated to minimize the loss function.
  - Update rule:
    - \( w_{new} = w_{old} - \eta \cdot \nabla w \)
    - \( \eta \): Learning rate, determining the step size for updates.
    - \( \nabla w \): Gradient of the loss with respect to the weight.
  - Repeated iterations of forward and backward passes refine the weights, improving the network’s predictions.

## 2. Applications

- **Backpropagation in Feedforward Neural Networks**
  - Feedforward networks use backpropagation to train weights across fully connected layers.
  - Applications:
    - Image classification, where layers progressively learn hierarchical features.
    - Regression tasks, such as predicting house prices based on input features.

- **Backpropagation Through Time (BPTT) for Recurrent Networks**
  - An extension of backpropagation for sequential data in RNNs.
  - Handles dependencies across time steps by unrolling the network across the sequence.
  - Steps:
    - Forward pass through the entire sequence to compute the output and loss.
    - Backward pass through the unrolled network to compute gradients across all time steps.
  - Challenges:
    - High memory requirements for storing intermediate states across time steps.
    - Risk of vanishing or exploding gradients in long sequences.

- **Examples**
  - **Gradient Calculation**:
    - Example: A small network with a single hidden layer calculates the loss gradients for weights and biases using backpropagation.
  - **Error Minimization**:
    - Example: Minimizing cross-entropy loss in a binary classification task using iterative updates of weights.
  - **Training Small Networks**:
    - Example: A simple XOR classification problem solved using backpropagation, demonstrating the power of non-linear activation functions.
