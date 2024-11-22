
## 1. Mathematical Foundations

- **[[Scalars, Vectors, Matrices, and Tensors]]**
  - **Scalars**:
    - Single numerical values, such as `x = 5`.
  - **Vectors**:
    - One-dimensional arrays representing magnitudes and directions, such as:
      ```
      v = [x1, x2, x3]
      ```
  - **Matrices**:
    - Two-dimensional arrays of numbers used for linear transformations:
      ```
      A = [ a11  a12 ]
          [ a21  a22 ]
      ```
  - **Tensors**:
    - Generalizations of matrices to higher dimensions, used for multi-dimensional data like images or videos.

- **Operations: Matrix Transpose, Dot Product, and Inversion**
  - **Matrix Transpose**:
    - Flips a matrix over its diagonal. Example:
      ```
      A = [ 1  2 ]     A^T = [ 1  3 ]
          [ 3  4 ]            [ 2  4 ]
      ```
  - **Dot Product**:
    - Computes the scalar product of two vectors. Formula:
      ```
      a · b = Σ (ai * bi)
      ```
  - **Matrix Inversion**:
    - Produces a matrix \( A^{-1} \) such that:
      ```
      A * A^-1 = I
      ```
      (where \( I \) is the identity matrix).
    - Used for solving systems of linear equations and transformations.

- **Vector Spaces and Their Properties**
  - **Definition**:
    - A set of vectors that can be scaled and added together to form other vectors in the same space.
  - **Properties**:
    - Closed under addition and scalar multiplication.
    - Contains a zero vector (neutral element for addition).
  - **Example**:
    - Linear combinations of basis vectors form a vector space.

## 2. Introduction to Neural Networks

- **Perceptron: Structure, Components, and Binary Classification**
  - **Structure**:
    - A single-layer neural network with one or more input nodes connected to an output node.
  - **Components**:
    - **Input Nodes**: Represent features of the input data.
    - **Weights**: Associated with each input to determine its importance.
    - **Bias**: A constant added to the weighted sum to shift the activation function.
    - **Activation Function**: Maps the weighted sum to the output.
  - **Binary Classification**:
    - Perceptrons classify input into one of two classes using a step function:
      ```
      Output = 1 if (w · x + b > 0), else 0
      ```

- **[[Activation Functions]]**
  - **Sigmoid**:
    - Maps inputs to the range (0, 1). Formula:
      ```
      σ(x) = 1 / (1 + e^(-x))
      ```
  - **ReLU (Rectified Linear Unit)**:
    - Outputs `0` for negative inputs and the input itself for positive inputs:
      ```
      ReLU(x) = max(0, x)
      ```
  - **Tanh**:
    - Maps inputs to the range (-1, 1). Formula:
      ```
      tanh(x) = (e^x - e^(-x)) / (e^x + e^(-x))
      ```
  - **Step Function**:
    - Outputs `0` or `1` based on whether the input is below or above a threshold.

- **Basics of Feedforward Neural Networks**
  - **Structure**:
    - Consists of an input layer, one or more hidden layers, and an output layer.
  - **Working**:
    - Data flows in a single direction (forward pass), from input to output.
    - Each layer applies weighted connections, biases, and activation functions.
  - **Applications**:
    - Used in tasks like image classification, regression, and feature extraction.
