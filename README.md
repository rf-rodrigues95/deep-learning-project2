# Deep Learning Project: Deep Reinforcement Learning for Snake Game  
**NOVA School of Science and Technology (NOVA FCT) – 2024/2025**  
**Course:** Deep Learning  
**Final Grade:** 17.5









**Group:** 
  - Ricardo Rodrigues (rf-rodrigues95)
  - Guilherme Antunes (gpantunes)
  - David Castro (DavidJCCastro)
---

## Objective

This project provides hands-on experience with deep reinforcement learning (RL) by training an agent to play a variant of the Snake game. The focus is on experimenting with different scenarios, training approaches, and understanding what helps the agent learn effectively.

## Repository Structure

- **./project2.ipynb** # Main Jupyter notebook that walks through the implementation, training, and evaluation of all project tasks. Serves as the central script for experimentation and results.
- **/environment/** # Python source files for the Snake game (snake_game.py) and a demo/test runner (game_demo.py). These define and initialize the game environment used during training and evaluation.
- **/report/** # Final comprehensive report covering all tasks (PDF)

---

## Game Overview and Setup

The environment is a Snake game implemented in the `SnakeGame` class with these main methods:

- `reset()`: Starts a new game and returns the initial state.
- `step(action)`: Executes an action and returns `(next_state, reward, done, info)`.

### Actions

The `step(action)` method accepts one of three discrete actions:

- `-1`: Turn snake left
- `0`: Keep moving straight
- `1`: Turn snake right

The effect depends on the current direction of the snake.

### Configurable Game Parameters

You can customize the game board when initializing `SnakeGame`:

SnakeGame(
  - width,               # Width of free region on the board
  - height,              # Height of free region on the board
  - food_amount,       # Number of food items
  - border,            # Border thickness (gray cells)
  - grass_growth,      # Growth rate of grass per step
  - max_grass          # Max grass per location
)

---

## Reinforcement Learning Components

### Deep Q-Network (DQN)

- **Inputs:** State images of the game board.
- **Outputs:** Q-values for each possible action.
- **Loss:** Q-learning loss using the Bellman equation:

$$
\text{Loss} = \left( r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right)^2
$$

Training incorporates experience replay and target networks for stability.

---

## Exploration Strategies

Two exploration methods should be implemented and compared:

- **Epsilon-Greedy:**  
  Action with highest Q-value chosen with probability \(1 - \epsilon\), random action with probability \(\epsilon\). Epsilon decays over time.

- **Boltzmann Exploration:**  
  Actions selected probabilistically via softmax over Q-values with temperature parameter \(T\):

$$
P(a_i) = \frac{\exp(Q(a_i) / T)}{\sum_j \exp(Q(a_j) / T)}
$$

---

## Project Tasks

### 1. Basic DQN Implementation

- Build a convolutional neural network suitable for processing board images.
- Implement the Q-learning loss.
- Train the agent without experience replay or target networks.
- Implement a heuristic policy to generate better training examples.
- Training constrained to 4 hours.

---

### 2. Enhanced DQN with Experience Replay and Target Network

- Implement an experience replay buffer (capacity ≤ 10,000).
- Implement a target network updated every ~100 steps.
- Integrate replay buffer into training loop.
- Experiment with buffer sizes and update strategies.

---

### 3. Exploration Strategies Comparison

- Implement and test epsilon-greedy with different decay schedules.
- Implement and test Boltzmann exploration with temperature scheduling.
- Compare both on:
  - Learning efficiency.
  - Final performance.
  - Exploration behavior.
  - Stability.
  - Hyperparameter sensitivity.

