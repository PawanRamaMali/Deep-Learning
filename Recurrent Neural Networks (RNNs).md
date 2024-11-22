
## 1. Basics of RNNs

- **Sequential Data Modeling**
  - RNNs are specialized neural networks designed to process sequential or time-series data.
  - Unlike feedforward networks, RNNs can capture temporal dependencies by using their internal state to remember information from previous time steps.
  - Applications:
    - Natural Language Processing (NLP): Predicting the next word in a sentence.
    - Time-Series Forecasting: Stock market prediction, weather forecasting.
    - Sequential Decision-Making: Robotics and reinforcement learning tasks.

- **Hidden States and Time-Step Dependencies**
  - Hidden State:
    - A core component of RNNs, updated at each time step to retain information about the sequence so far.
    - Formula: \( $h_t = f(Wx_t + Uh_{t-1} + b)$ \), where:
      - \( $x_t$ \): Input at time \( $t$ \).
      - \( $h_{t-1}$ \): Hidden state from the previous time step.
      - \( $f$ \): Activation function (commonly tanh or ReLU).
  - Time Dependencies:
    - Captures short-term and long-term relationships in sequential data.
    - Example: In a language model, the meaning of a word may depend on the context provided by previous words.

## 2. Advanced RNN Models

- **Long Short-Term Memory (LSTM)**
  - Structure:
    - Introduces a **cell state** to store long-term information and manage what to retain or forget.
    - Includes gates to regulate the flow of information:
      - Forget Gate: Decides what information to discard from the cell state.
      - Input Gate: Updates the cell state with new information.
      - Output Gate: Determines the hidden state output.
  - Benefits:
    - Solves vanishing gradient problems by maintaining gradients over long sequences.
    - Effective for tasks requiring long-term memory, such as speech recognition and text generation.

- **Gated Recurrent Unit (GRU)**
  - Structure:
    - A simplified version of LSTM with fewer parameters, combining the forget and input gates into a single update gate.
    - Lacks a separate cell state, using the hidden state to manage memory.
  - Benefits:
    - Computationally efficient while retaining effectiveness for many tasks.
    - Suitable for resource-constrained applications like mobile devices.
  - Use Cases:
    - Machine translation, video captioning, and online recommendation systems.

## 3. Training Techniques

- **Addressing Vanishing Gradients**
  - The vanishing gradient problem occurs when gradients diminish as they are backpropagated through many time steps.
  - Techniques to mitigate this:
    - Using advanced architectures like LSTM and GRU.
    - Gradient clipping to cap excessively large gradients and stabilize training.
    - Careful initialization of weights to prevent extreme values during backpropagation.

- **Backpropagation Through Time (BPTT)**
  - BPTT is an extension of backpropagation applied to RNNs to compute gradients across time steps.
  - Steps:
    1. Perform a forward pass for the entire sequence, storing intermediate states.
    2. Compute the loss at the end of the sequence.
    3. Backpropagate the loss through time steps to calculate gradients for weights and biases.
  - Challenges:
    - High computational cost for long sequences due to the need to store states for every time step.
    - Risk of exploding or vanishing gradients, especially for long sequences.
  - Applications:
    - Speech recognition: Mapping audio waveforms to text.
    - Sentiment analysis: Understanding the tone of text across multiple sentences.
