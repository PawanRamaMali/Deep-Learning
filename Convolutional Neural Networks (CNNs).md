

## 1. Introduction to CNNs

- **Components**
  - **Convolutional Layers**:
    - Core building blocks of CNNs, responsible for feature extraction.
    - Use filters (kernels) that slide over the input data, applying element-wise multiplications to extract localized features.
    - Captures spatial hierarchies (e.g., edges, textures, and complex patterns).
  - **Pooling Layers**:
    - Reduce the spatial dimensions of the data to decrease computational complexity and enhance robustness.
    - Types:
      - Max Pooling: Selects the maximum value in each region.
      - Average Pooling: Computes the average of values in each region.
    - Helps retain dominant features while discarding less relevant details.
  - **Fully Connected Layers**:
    - Positioned after convolutional and pooling layers to map extracted features to the output labels.
    - Perform final classification or regression tasks.

- **Feature Extraction Using Kernels and Filters**
  - Filters:
    - Small matrices that detect specific features like edges, gradients, or patterns.
    - Slide across the input image to produce feature maps.
  - Strides and Padding:
    - Strides determine the step size for filter movement.
    - Padding adds borders to maintain the input's original dimensions.
  - Hierarchical Learning:
    - Initial layers capture basic features (e.g., edges), while deeper layers capture more complex features (e.g., objects).

## 2. Architectures and Applications

- **Famous Architectures**
  - **AlexNet**:
    - Revolutionized deep learning in 2012 by winning the ImageNet Challenge.
    - Features: ReLU activation, dropout for regularization, and overlapping pooling.
  - **VGG**:
    - Known for simplicity and uniform design, with smaller (3x3) filters stacked sequentially.
    - Achieves high accuracy but is computationally intensive.
  - **GoogLeNet (Inception Network)**:
    - Introduced inception modules, which combine filters of different sizes to capture multi-scale features.
    - Efficient in terms of computational resources.
  - **ResNet**:
    - Introduced residual connections to address the vanishing gradient problem.
    - Enables training of very deep networks by allowing gradients to flow unimpeded.

- **Use Cases**
  - **Object Detection**:
    - Identifies and localizes objects within images.
    - Applications: Autonomous vehicles (pedestrian detection), surveillance systems.
  - **Style Transfer**:
    - Transfers artistic styles from one image to another (e.g., converting a photo into a painting style).
  - **Super-Resolution**:
    - Enhances low-resolution images to higher quality while preserving details.
    - Applications: Satellite imagery, medical imaging.

## 3. Training CNNs

- **Backpropagation for Weight Updates**
  - Gradient computation:
    - Gradients are computed for convolutional layers, pooling layers, and fully connected layers.
    - Convolutional layer gradients are calculated for both weights (filters) and biases.
  - Update rules:
    - Weights are updated using optimization algorithms like SGD or Adam based on the calculated gradients.
  - Loss functions:
    - Cross-entropy for classification tasks.
    - Mean Squared Error (MSE) for regression or reconstruction tasks.

- **Shared Weights and Localized Feature Extraction**
  - Shared Weights:
    - Filters are reused across the entire input, significantly reducing the number of parameters compared to fully connected networks.
    - Enhances efficiency and prevents overfitting for large inputs.
  - Localized Features:
    - Convolutional layers focus on small, overlapping regions of the input, capturing spatial relationships.
    - Pooling layers ensure invariance to small translations in the input data, improving robustness.
