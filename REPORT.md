# Deep Neural Network Architecture

The deep neural network that was used consisted of 3 fully connected layers. This was implemented in PyTorch. ReLU units were used as activation units.

# Algorithm

The algorithm that was used to implement this is the Deep Q Learning algorithm. The full algorithm is outlined in the [Deep Q Network](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) paper

The algorithm can be summarized as follows:
* We need a replay memory to hold the previously played steps and outcomes. We initialize this memory `D` to some capacity `N`.
* We create two networks, viz. the local Q-Network and the target Q-Network. The local Q-Network is the one that is continously being trained and every few iterations or so we copy the weights to the target Q-Network that is used to set the target to which the local network is learning. However, it is important to note that the local Q-Network is the one that finally approximates the Q function.
* We then start the training of the agent for as many episodes required so that the training criteria is met. Each episode is represented by either the number of t_steps defined in the method or when the episode is terminated by the environment, whichever is earlier. 
* The training process consists of
  * The agent acting by taking the appropriate step according to the SARSA Max approach. Everytime, it takes the action which results in the maximum Q value according the current state and the local Q-Network.
  * The environment when presents the next state and reward to the agent by receiving the step by the agent.
  * The state `S`, action `A`, reward `R`, next_state `S'` is added to the replay memory.
  * As the agent is continously interacting with the environment, the replay memory is continuously sampled and the agent learns the weights of the local Q-Network. The sampling is done in a uniform way.
- We use a minibatch os experience replays to learn the weights and the loss function is represented by the mean squared error between the Q value from the local Q-Network and the desired Q value from the target network.
- When copying the weights from the local Q-Network and the target Q-Network, we do a soft copy.

# Hyperparameters
The following hyperparameters were used by the implementation.
```
n_episodes = 1000
BUFFER_SIZE = int(1e5) # replay memory capacity
BATCH_SIZE = 64 # minibatch size. the number of experiences trained at a time
GAMMA = 0.99 # discount factor
TAU = 1e-3 # factor by which the soft update of the weights from local to target
LR = 5e-4 # learning rate for the optimizer
UPDATE_EVERY = 5 # updating the weights onto target every 5 iterations
optimizer = ADAM # adam optimizer for learning
```

# Results
The average reward collection over 100 episodes plotted in a graph below. It shows the average reward on the Y axis for every point on the X axis representing any 100 consecutive episodes.

## Performance Graph
![](images/dqn_banana_trained_agent.png)

## Trained Agent
I have recorded a video of the trained agent in action. To watch the video please click on the below image.

[![Trained Agent](https://img.youtube.com/vi/iLqFUZT3pVY/0.jpg)](https://www.youtube.com/watch?v=iLqFUZT3pVY)
