
## Introduction

Activation functions are crucial in neural networks. They introduce non-linearity, enabling the network to learn complex patterns. Without activation functions, the network would be equivalent to a linear regression model, no matter the number of layers.

---

## Types of Activation Functions

### 1. **Linear Activation Function**

- **Equation:** \( $f(x) = x$ \)
- **Characteristics:**
  - Output is proportional to input.
  - Used in specific tasks like regression.
  - **Limitation:** Cannot introduce non-linearity.
  
---

### 2. **Sigmoid Function**

- **Equation:** 
    $f(x) = \frac{1}{1 + e^{-x}}$
- **Range:** \( (0, 1) \)
- **Use Cases:** Binary classification tasks.
- **Advantages:**
  - Smooth gradient.
  - Output values are normalized.
- **Disadvantages:**
  - Vanishing gradient problem.
  - Computationally expensive due to the exponential function.

---

### 3. **Hyperbolic Tangent (Tanh)**

- **Equation:** 
  \[
  $f(x) = \tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$
  \]
- **Range:** \( (-1, 1) \)
- **Use Cases:** Hidden layers in neural networks.
- **Advantages:**
  - Centered at 0, making optimization easier.
  - Smooth gradient.
- **Disadvantages:**
  - Suffers from vanishing gradient problem for large values.

---

### 4. **Rectified Linear Unit (ReLU)**

- **Equation:** 
  \[
  $f(x) = \max(0, x)$
  \]
- **Range:** \( $[0, \infty)$ \)
- **Use Cases:** Most common activation function in hidden layers.
- **Advantages:**
  - Efficient computation.
  - Helps mitigate the vanishing gradient problem.
- **Disadvantages:**
  - Can suffer from the "dying ReLU" problem where neurons output zero and stop learning.

---

### 5. **Leaky ReLU**

**Equation:**

$$
f(x) = 
\begin{cases} 
x, & \text{if } x > 0 \\
\alpha x, & \text{if } x \leq 0
\end{cases}
$$

where \( $\alpha$ \) is a small constant (e.g., \( 0.01 \)).

- **Range:** \( ($-\infty, \infty$) \)
- **Advantages:**
  - Addresses the "dying ReLU" problem.
- **Disadvantages:**
  - Selection of \( $\alpha$ \) can be arbitrary.

---

### 6. **Softmax Function**

- **Equation:** 
  
  $f_i(x) = \frac{e^{x_i}}{\sum_{j} e^{x_j}}$
  
- **Use Cases:** Multi-class classification in the output layer.
- **Advantages:**
  - Converts logits into probabilities.
  - Ensures outputs sum to 1.
- **Disadvantages:**
  - Can amplify outliers in the data.

---

## Comparison of Activation Functions

| **Function** | **Range**               | **Computational Cost** | **Gradient Issue**     | **Applications**                  |
| ------------ | ----------------------- | ---------------------- | ---------------------- | --------------------------------- |
| Linear       | \( $-\infty, \infty$ \) | Low                    | No gradient saturation | Regression tasks                  |
| Sigmoid      | \( 0, 1 \)              | High                   | Vanishing gradient     | Binary classification             |
| Tanh         | \( -1, 1 \)             | High                   | Vanishing gradient     | Hidden layers                     |
| ReLU         | $[0, \infty)$           | Low                    | Dying ReLU problem     | Most neural network architectures |
| Leaky ReLU   | ($-\infty, \infty$)     | Low                    | Minimal                | Deep networks                     |
| Softmax      | (0, 1)                  | High                   | None                   | Output layers for classification  |
|              |                         |                        |                        |                                   |

---

## Examples
### Example 1: Sigmoid
Given \( x = 2 \), compute \( f(x) \):
\[
$f(2) = \frac{1}{1 + e^{-2}} \approx 0.88$
\]

### Example 2: Tanh
For \( x = 1 \):
\[
$f(1) = \tanh(1) = \frac{e^1 - e^{-1}}{e^1 + e^{-1}} \approx 0.76$
\]

### Example 3: ReLU
For \( x = -3 \) and \( x = 2 \):
\[
$f(-3) = \max(0, -3) = 0,\ f(2) = \max(0, 2) = 2$
\]

---

## Choosing the Right Activation Function

- **Output Layers:**
  - Use **Sigmoid** for binary classification.
  - Use **Softmax** for multi-class classification.
- **Hidden Layers:**
  - Use **ReLU** or its variants for most applications.
  - Consider **Tanh** for tasks requiring zero-centered activation.

---

## Summary

Activation functions play a pivotal role in deep learning by introducing non-linear properties, enabling the network to model complex relationships in data. Selection of the appropriate activation function depends on the problem domain and architecture.

 [Back](README)