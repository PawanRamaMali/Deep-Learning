# Model Interpretability and Explainability

## 1. Feature Visualization Techniques

### Activation Visualization
```python
def visualize_activation(model, layer_name, filter_index):
    layer_output = model.get_layer(layer_name).output
    loss = K.mean(layer_output[:, :, :, filter_index])
    grads = K.gradients(loss, model.input)[0]
    iterate = K.function([model.input], [loss, grads])
```

### Class Activation Maps (CAM)
- **Gradient-weighted Class Activation Mapping (Grad-CAM)**
  - Highlights regions contributing to specific predictions
  - Formula: αᵏₖ = Σᵢⱼ ∂y/∂Aᵏᵢⱼ
  - Implementation:
    ```python
    def grad_cam(model, image, class_idx):
        grad_model = tf.keras.models.Model(
            [model.inputs], 
            [model.get_layer(last_conv_layer).output, model.output]
        )
        with tf.GradientTape() as tape:
            conv_output, predictions = grad_model(image)
            loss = predictions[:, class_idx]
        grads = tape.gradient(loss, conv_output)
    ```

### Feature Attribution Maps
1. **Integrated Gradients**
   - Baseline comparison
   - Path integral computation
   - Attribution scores for each feature

2. **Saliency Maps**
   - Gradient-based importance
   - Pixel-level contributions
   - Visual explanation of decisions

## 2. Attribution Methods

### SHAP (SHapley Additive exPlanations)
```python
import shap
explainer = shap.DeepExplainer(model, background_data)
shap_values = explainer.shap_values(test_data)
```

- **Key Components**:
  1. Kernel SHAP
     - Model-agnostic
     - Coalitional game theory
     - Feature importance values
  
  2. Deep SHAP
     - Neural network specific
     - Backpropagation-based
     - Layer-wise relevance

### LIME (Local Interpretable Model-agnostic Explanations)
```python
from lime import lime_image
explainer = lime_image.LimeImageExplainer()
explanation = explainer.explain_instance(
    image, 
    classifier_fn,
    top_labels=5, 
    hide_color=0, 
    num_samples=1000
)
```

- **Process**:
  1. Sample perturbations
  2. Get predictions
  3. Fit local interpretable model
  4. Extract feature importance

## 3. Concept Attribution

### Testing with Concepts (TCAV)
1. **Concept Definition**
   ```python
   def define_concept(concept_examples):
       return train_concept_classifier(concept_examples)
   ```

2. **Sensitivity Testing**
   - Directional derivatives
   - Concept activation vectors
   - Statistical significance

### Concept Bottleneck Models
```python
class ConceptBottleneckModel(Model):
    def __init__(self):
        self.concept_layer = Dense(n_concepts)
        self.task_layer = Dense(n_classes)
    
    def call(self, inputs):
        concepts = self.concept_layer(inputs)
        outputs = self.task_layer(concepts)
        return outputs
```

## 4. Adversarial Examples and Robustness

### Attack Methods
1. **Fast Gradient Sign Method (FGSM)**
   ```python
   def fgsm_attack(image, epsilon, data_grad):
       perturbed_image = image + epsilon * sign(data_grad)
       return clip(perturbed_image, 0, 1)
   ```

2. **Projected Gradient Descent (PGD)**
   ```python
   def pgd_attack(model, x, y, epsilon, alpha, num_iter):
       delta = torch.zeros_like(x, requires_grad=True)
       for _ in range(num_iter):
           loss = nn.CrossEntropyLoss()(model(x + delta), y)
           loss.backward()
           delta.data = (delta + alpha*delta.grad.sign()).clamp(-epsilon, epsilon)
           delta.grad.zero_()
   ```

### Defense Strategies

1. **Adversarial Training**
```python
def adversarial_train_step(model, x_batch, y_batch):
    # Generate adversarial examples
    x_adv = generate_adversarial_examples(model, x_batch)
    
    # Combined training
    loss = 0.5 * (model.train_on_batch(x_batch, y_batch) +
                  model.train_on_batch(x_adv, y_batch))
```

2. **Defensive Distillation**
- Train teacher model normally
- Use soft labels for student model
- Temperature scaling in softmax

### Robustness Metrics
1. **Empirical Robustness**
   - Success rate of attacks
   - Perturbation magnitude
   - Coverage of attack space

2. **Certified Robustness**
   - Formal verification
   - Lipschitz constants
   - Provable bounds

## 5. Best Practices

1. **Interpretation Pipeline**
   - Multiple complementary methods
   - Cross-validation of explanations
   - Human-in-the-loop verification

2. **Robustness Assessment**
   - Diverse attack methods
   - Multiple perturbation types
   - Evaluation across datasets

3. **Documentation**
   - Model cards
   - Explanation reliability
   - Known limitations
