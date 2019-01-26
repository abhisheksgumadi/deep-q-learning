# Deep Neural Network Architecture

The deep neural network that was used consisted of 3 fully connected layers. This was implemented in PyTorch. ReLU units were used as activation units.

# Algorithm

The algorithm that was used to implement this is the Deep Q Learning algorithm. The full algorithm is outlined in the [Deep Q Network](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) paper

The algorithm can be summarized as follows:
- We need a replay memory to hold the previously played steps and outcomes. We initialize this memory `D` to some capacity `N`.
- We initialize the local Q-Network (which should approximate the true action-value function Q) with random weights (using PyTorch default weight initialization for any module).
- We copy those generated weights to the target Q-Network (which shall be updated every some defined number of iterations).
- We train the agent for some episodes and for some maximum number of time-steps (max_t) in each episode, unless it terminates earlier (e.g. by encountering a terminal state).
- The training loop is composed out of two steps: sampling and learning.
- In the sampling step, the agent follows a behavioral (epsilon-greedy) policy, which given a state s returns an action a. It executes this action a and observes reward r and next state s'. The experince tuple (s, a, r, s', d), where d is a boolean flag which denotes whether the episode will terminate in state s', is stored in the replay buffer D.
- In the learning step, the agent samples uniformly at random a mini-batch of experience tuples from D.
- It uses these experience tuples to compute the targets by following a target (greedy) policy. The mean squared error between the target and expected action-values is computed and this TD-error is backpropagated in the local Q-Network so to update the weights using one step of SGD.
- Next, we update the target Q-Network weights by making a copy of the current weights of the local Q-Network.

# Hyperparameters


# Results

## Performance Graph

## Trained Agent

# Potential Improvements
