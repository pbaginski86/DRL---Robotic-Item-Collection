# Udacity Deep Reinforcement Learning Nanodegree - Project 1 "Banana Collector Robot"

## Overview

This report describes the implementation of a simple, out-of-the-box Deep Q-Learning algorithm to the problem of robotic navigation
in a squared game-like world. The project is based on Unity's Banana Collector environment and instructions on how to
copy this implementation can be found in the README file in this repository.

This implementation is based on a few famed research papers, especially the below:

- **DQN**: Mnih, Volodymyr, et al. "Human-level control through deep reinforcement learning." Nature 518.7540 (2015): 529.

## Learning Algorithm

The algorithm implemented is called the Deep Q-Learning algorithm. It is a combination of a simple temporal-difference based
Reinforcement Learning algorithm called Q-Learning, combined with a deep learning network to approximate the
q-action-value-function. In detail what this means is that the agent learns the best action-value by approximation through a
neural network. This implies in itself some areas for improvement that have been vastly discussed in above papers: Prioritized
experience replay, double DQN, dueling DQN, fixed Q-targets and e.g. learning-rate decay.

The traditional DQN algorithm approximates a chosen action (and score for collecting bananas) in the following way:

- At every time step, the state is provided to the agent and the agent selects an action following an epsilon-greedy action selection.
- One the action is returned, the next state of the environment is observed and the reward is collected, as described in the README.
- The experience tuple of State, action, next state and the reward is provided to the agent for learning purposes. The tuple is also added to the replay memory, from which random samples are chosen to continue the learning process.

## Q-network architecture

The architecture for the above algorithm is based on a deep Q-network which maps a state to a Q-value for each possible action.
The DQN implementation uses a neural network with six hidden layers that have slightly assymetrical node distribution (going from 37 states to 64 nodes, to 128, then to 64, 32 and finally 4 action values) using rectified linear unit activation. function. The complete architecture can be found in the README.

## Hyperparameters

| Hyperparameter | Value | Description |
|---|---:|---|
| Replay memory size | 100000 | Maximum size of experience replay memory |
| Replay batch size | 64 | Number of experiences sampled in one batch |
| Q-network hidden sizes | 64, 128, 64, 32 | Number of nodes in hidden layers of the Q-networks |
| Learning frequency | 4 | Number of steps between learning occurs |
| Learning  rate | 0.0005 | Controls parameters update of the online Q-network |
| Discount factor | 0.99 | Discount rate for future rewards |
| Target update freq | 1 | Number of learning steps between parameter updates of the target Q-network |
| Soft update factor | 0.001 | Controls parameters update of the target Q-network from the online Q-network |
| Epsilon start | 1.0 | Start value for the epsilon parameter in epsilon-greedy strategy |
| Epsilon end | 0.01 | Final value for the epsilon parameter in epsilon-greedy strategy |
| Epsilon decay | 0.995 | Decrease of the epsilon parameter in epsilon-greedy strategy |

Values for the hyperparameters were obtained from the papers and kept as-is to keep the algorithm as much "out-of-the-box" as possible. A systematic approach could help in determining better sets of hyperparameters, however, the algorithm would need to be improved in terms of training time, e.g. through batch normalization.

## Results

The environment was solved bby the agent collecting more than 13 bananas over 25 consecutive episodes in usually 400-500 episodes of training.

Plotting the results:

![Scores plot](result_score.jpeg)

## Potential improvements

Please see the README and above section for areas for potential improvement.



