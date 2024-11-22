

## 1. Deep Neural Networks (DNNs)

- **Structure of DNN**
  - **Input Layer**:
    - The first layer in the network receives raw input data (e.g., images, text, numerical values).
    - Each neuron in the input layer corresponds to a feature of the input data.
  - **Hidden Layers**:
    - Intermediate layers that process input data through weighted connections and activation functions.
    - Multiple hidden layers allow DNNs to learn complex patterns and hierarchical representations.
    - Features:
      - Each layer extracts progressively higher-level features from the input.
      - Non-linear activation functions (e.g., ReLU, Sigmoid, Tanh) introduce non-linearity to the model.
  - **Output Layer**:
    - Produces the final predictions based on the learned features.
    - The number of neurons in the output layer corresponds to the task:
      - Single neuron for binary classification.
      - Multiple neurons for multi-class classification or regression.

- **Challenges in Training Deep Networks**
  - **Vanishing Gradients**:
    - Gradients become very small as they are backpropagated through many layers, leading to slow or stalled weight updates.
    - Common in networks with Sigmoid or Tanh activation functions.
  - **Exploding Gradients**:
    - Gradients grow excessively large during backpropagation, causing instability and divergence.
    - Often occurs in RNNs or when weights are poorly initialized.
  - Solutions:
    - Advanced architectures like LSTMs for sequential data.
    - Gradient clipping to prevent gradients from exceeding a threshold.
    - Batch normalization to stabilize training dynamics.

## 2. Training Techniques

- **Regularization Methods**
  - Techniques to prevent overfitting and improve generalization:
    - **Weight Decay (L2 Regularization)**:
      - Penalizes large weights by adding a term proportional to their squared magnitude to the loss function.
    - **Dropout**:
      - Randomly drops neurons during training to prevent reliance on specific features.
      - Effective in reducing overfitting in large networks.
    - **Batch Normalization**:
      - Normalizes layer inputs to a standard distribution, stabilizing gradients and speeding up training.
      - Acts as a form of regularization by introducing noise during training.

- **Early Stopping**
  - Monitors the model’s performance on a validation set during training.
  - Stops training when validation performance ceases to improve, preventing overfitting.
  - Benefits:
    - Reduces computation time.
    - Ensures the model is not overly tailored to the training data.

- **Optimization Algorithms**
  - Methods for updating weights to minimize the loss function:
    - **Stochastic Gradient Descent (SGD)**:
      - Updates weights using the gradient of the loss function for a single training example.
      - Benefits: Simple and efficient for large datasets.
      - Challenges: Noisy updates can lead to slow convergence.
    - **Adam (Adaptive Moment Estimation)**:
      - Combines momentum and adaptive learning rates for faster convergence.
      - Adjusts the learning rate for each parameter based on past gradients.
    - **RMSProp**:
      - Maintains a moving average of squared gradients to normalize updates.
      - Well-suited for non-stationary objectives like RNNs.

- **Mini-Batch Gradient Descent**
  - Divides the training data into small batches, performing weight updates for each batch.
  - Advantages:
    - Balances efficiency (compared to batch gradient descent) and stability (compared to SGD).
    - Introduces regularization through mini-batch sampling, reducing overfitting.
  - Widely used in modern deep learning frameworks due to its scalability and robustness.
