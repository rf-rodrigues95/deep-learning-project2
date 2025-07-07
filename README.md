# Project 2: Deep Reinforcement Learning for Snake Game

## Objective

This project provides hands-on experience with deep reinforcement learning (RL) by training an agent to play a variant of the Snake game. The focus is on experimenting with different scenarios, training approaches, and understanding what helps the agent learn effectively.

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

```python
SnakeGame(
  width,               # Width of free region on the board
  height,              # Height of free region on the board
  food_amount,       # Number of food items
  border,            # Border thickness (gray cells)
  grass_growth,      # Growth rate of grass per step
  max_grass          # Max grass per location
)
