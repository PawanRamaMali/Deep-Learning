# Deep Reinforcement Learning

## 1. Policy Gradients

### Core Concepts
- Direct optimization of policy parameters to maximize expected return
- Uses gradient ascent on policy parameters
- Policy represented by neural network that maps states to action probabilities

### REINFORCE Algorithm
- Monte Carlo policy gradient method
- Updates policy parameters using complete episode returns
- High variance but unbiased gradient estimates
- Uses baseline subtraction for variance reduction

### Advanced Policy Gradient Methods
- Trust Region Policy Optimization (TRPO)
  - Constrains policy updates to improve stability
  - Uses KL-divergence constraint
  - Guarantees monotonic improvement

- Proximal Policy Optimization (PPO)
  - Simpler alternative to TRPO
  - Clips probability ratio to limit policy changes
  - Better sample efficiency and easier implementation

## 2. Q-Learning and DQN

### Q-Learning Fundamentals
- Value-based method learning action-value function
- Updates Q-values using temporal difference learning
- Balances exploration and exploitation
- Guaranteed convergence in tabular case

### Deep Q-Network (DQN)
- Uses neural network to approximate Q-function
- Key innovations:
  - Experience replay buffer
  - Target network
  - Frame stacking
  - Reward clipping

### DQN Improvements
- Double DQN: Reduces overestimation bias
- Dueling DQN: Separate advantage and value streams
- Prioritized Experience Replay: Important transitions sampled more frequently
- Rainbow DQN: Combines multiple improvements

## 3. Actor-Critic Methods

### Architecture
- Actor: Policy network determining actions
- Critic: Value network evaluating actions
- Reduces variance compared to pure policy gradients
- Enables online updates unlike Monte Carlo methods

### Variants
1. Advantage Actor-Critic (A2C)
   - Uses advantage function to reduce variance
   - Synchronous version of A3C
   - Better sample efficiency than policy gradients

2. Asynchronous Advantage Actor-Critic (A3C)
   - Parallel training using multiple agents
   - Shares network parameters across agents
   - Improved exploration through diversity

3. Soft Actor-Critic (SAC)
   - Maximum entropy framework
   - Off-policy training
   - Automatic entropy adjustment
   - State-of-the-art performance on continuous control

## 4. Applications

### Robotics
1. Manipulation Tasks
   - Grasping and picking
   - Assembly operations
   - Tool manipulation
   - Challenges: Sample efficiency, real-world transfer

2. Motion Planning
   - Trajectory optimization
   - Obstacle avoidance
   - Dynamic environments
   - Safety constraints

### Game Playing
1. Atari Games
   - End-to-end learning from pixels
   - Discrete action spaces
   - Visual processing
   - Long-term credit assignment

2. Board Games
   - Perfect information games (Chess, Go)
   - Imperfect information games (Poker)
   - Combination with search algorithms
   - Self-play training

### Key Challenges
1. Sample Efficiency
   - High data requirements
   - Real-world data collection costs
   - Simulation to reality transfer

2. Exploration
   - Sparse rewards
   - Long-term dependencies
   - Strategic exploration

3. Stability
   - Sensitive hyperparameters
   - Non-stationary training
   - Reproducibility issues

4. Safety and Constraints
   - Risk management
   - Constraint satisfaction
   - Robustness to perturbations
