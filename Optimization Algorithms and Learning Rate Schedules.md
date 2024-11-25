# Optimization Algorithms and Learning Rate Schedules

## 1. Optimization Algorithms

### Stochastic Gradient Descent (SGD)
```python
w = w - learning_rate * gradient
```
- **Basic Concept**: Updates parameters using gradients computed on mini-batches
- **Advantages**: 
  - Simple implementation
  - Low memory requirements
- **Limitations**:
  - Sensitive to learning rate selection
  - Can oscillate in ravines
  - May get stuck in local minima

### Momentum
```python
velocity = momentum * velocity - learning_rate * gradient
w = w + velocity
```
- **Purpose**: Accelerates SGD in relevant directions
- **Benefits**:
  - Reduces oscillations
  - Faster convergence
- **Typical momentum values**: 0.9 to 0.99

### Adam (Adaptive Moment Estimation)
```python
m = beta1 * m + (1 - beta1) * gradient  # First moment
v = beta2 * v + (1 - beta2) * gradient**2  # Second moment
m_hat = m / (1 - beta1**t)  # Bias correction
v_hat = v / (1 - beta2**t)
w = w - learning_rate * m_hat / (sqrt(v_hat) + epsilon)
```
- **Features**:
  - Adapts learning rates per parameter
  - Combines momentum and RMSprop
- **Default hyperparameters**:
  - β₁ = 0.9 (momentum)
  - β₂ = 0.999 (RMSprop factor)
  - ε = 1e-8 (numerical stability)

### AdaGrad
```python
accumulated_gradient = accumulated_gradient + gradient**2
w = w - learning_rate * gradient / (sqrt(accumulated_gradient) + epsilon)
```
- **Key Feature**: Adapts learning rate based on parameter history
- **Best Use Case**: Sparse data and features
- **Limitation**: Learning rate can become very small over time

## 2. Learning Rate Schedules

### Step Decay
```python
learning_rate = initial_lr * drop_factor**(floor(epoch / epochs_drop))
```
- Reduces learning rate by a factor after fixed number of epochs
- Example: Reduce by 0.5 every 10 epochs

### Exponential Decay
```python
learning_rate = initial_lr * exp(-decay_rate * epoch)
```
- Smoothly decreases learning rate over time
- Requires careful tuning of decay rate

### Cosine Annealing
```python
learning_rate = min_lr + 0.5 * (max_lr - min_lr) * (1 + cos(epoch * pi / total_epochs))
```
- Oscillates learning rate between maximum and minimum values
- Can be combined with restarts (SGDR)

## 3. Warm-up Schedules

### Linear Warm-up
```python
if epoch < warmup_epochs:
    lr = initial_lr * (epoch / warmup_epochs)
else:
    lr = regular_schedule(epoch)
```
- Gradually increases learning rate from small to target value
- Helps stabilize early training
- Typical duration: 5-10% of total training epochs

### Exponential Warm-up
```python
if epoch < warmup_epochs:
    lr = initial_lr * exp(log(target_lr/initial_lr) * epoch/warmup_epochs)
else:
    lr = regular_schedule(epoch)
```
- Smoother transition compared to linear warm-up
- Better for very deep networks

## 4. Curriculum Learning

### Implementation Strategies

1. **Data Complexity Progression**
```python
def get_curriculum_data(epoch):
    difficulty = min(1.0, epoch / total_curriculum_epochs)
    return select_samples_by_difficulty(training_data, difficulty)
```

2. **Task Complexity Progression**
```python
def get_curriculum_task(epoch):
    if epoch < epoch1:
        return simple_task
    elif epoch < epoch2:
        return intermediate_task
    else:
        return complex_task
```

### Common Approaches
- Start with easier examples/tasks
- Gradually increase difficulty
- Can be based on:
  - Sample length/complexity
  - Noise level
  - Task complexity
  - Data ambiguity

### Benefits
- Faster convergence
- Better final performance
- More stable training
- Improved generalization

## 5. Best Practices

1. **Optimizer Selection**
   - Adam for most cases
   - SGD + Momentum for state-of-the-art results
   - AdaGrad for sparse data

2. **Learning Rate Tuning**
   - Start with 3e-4 for Adam
   - Use learning rate finder when possible
   - Monitor loss curves for instability

3. **Schedule Selection**
   - Use warm-up for very deep networks
   - Cosine annealing for longer training
   - Step decay for simple cases

4. **Curriculum Design**
   - Define clear progression metrics
   - Avoid too rapid difficulty increase
   - Monitor validation performance
