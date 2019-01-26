# Deep Neural Network Architecture

The deep neural network that was used consisted of 3 fully connected layers. This was implemented in PyTorch. ReLU units were used as activation units.

# Algorithm

The algorithm that was used to implement this is the Deep Q Learning algorithm. The full algorithm is outlined in the [Deep Q Network](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) paper

The algorithm can be summarized as follows:
* We need a replay memory to hold the previously played steps and outcomes. We initialize this memory `D` to some capacity `N`.
* We create two networks, viz. the local Q-Network and the target Q-Network. The local Q-Network is the one that is continously being trained and every few iterations or so we copy the weights to the target Q-Network that is used to set the target to which the local network is learning. However, it is important to note that the local Q-Network is the one that finally approximates the Q function.
* We then start the training of the agent for as many episodes required so that the training criteria is met. Each episode is represented by either the number of t_steps defined in the method or when the episode is terminated by the environment, whichever is earlier. 
* The training process consists of
  * The agent acting by taking the appropriate step according to the SARSA Max approach.
  * The environment when presents the next state and reward to the agent by receiving the step by the agent.
  * The state, action, reward, next_state is added to the replay memory.
  * As the agent is continously interacting with the environment, the replay memory is continuously sampled and the agent learns the weights of the local Q-Network.
- In the sampling step, the agent follows a behavioral (epsilon-greedy) policy, which given a state s returns an action a. It executes this action a and observes reward r and next state s'. The experince tuple (s, a, r, s', d), where d is a boolean flag which denotes whether the episode will terminate in state s', is stored in the replay buffer D.
- In the learning step, the agent samples uniformly at random a mini-batch of experience tuples from D.
- It uses these experience tuples to compute the targets by following a target (greedy) policy. The mean squared error between the target and expected action-values is computed and this TD-error is backpropagated in the local Q-Network so to update the weights using one step of SGD.
- Next, we update the target Q-Network weights by making a copy of the current weights of the local Q-Network.

# Hyperparameters


# Results

## Performance Graph

## Trained Agent

# Potential Improvements
