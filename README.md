# Udacity Project 1 - Navigation

## Objective

To train a [Deep Q Learning](https://deepmind.com/research/dqn/) agent for the Banana collection game in UnityML agents

## Background

**Reward**: The agent geta a reward of +1 for collecting a yellow banana, and a reward of -1 for collecting a blue banana. Thus, the goal of the agent is to maximise the long term reward by collecting as many yellow bananas as possible while avoiding blue bananas.

**State**: Every state the agent is in can be represented by a vector that has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction. Given this information, the agent has to learn how to best select actions.

**Actions**: The agent can take four different actions namely,:

0 - move forward.
1 - move backward.
2 - turn left.
3 - turn right.

**Termination**: The agent terminated after taking 300 time steps.

In order to consider the environment has been solved, the agent must get an average score of +13 over 100 consecutive episodes.

## Getting Started

### Repository

Clone the repository - 
```bash
git clone https://github.com/abhisheksgumadi/deep-q-learning.git .
cd deep-q-learning
```

### Jupyter Notebook
Install jupyter notebook with the command
```
pip install jupyter
```
Then, open the Navigation.ipynb notebook

```
jupyter notebook Navigation.ipynb
```

### Banana Unity Environment
Download the Banana environment for Unity at [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)

## Code Overview
The code consists of the following modules
```
Navigation.ipynb - the main notebook
agent.py - defines the Agent that is being trained
model.py - defines the PyTorch model for the Deep Q Network
checkpoint.pth - is the final trained agent that has been trained to get atleast a reward of 13 points over 100 consecutive episodes
```

Please follow the code in Navigation.ipynb to train the agent

## Results

The average reward collection over 100 episodes plotted in a graph below. It shows the average reward on the Y axis for every point on the X axis representing any 100 consecutive episodes.


![](images/dqn_banana_trained_agent.png)

## Trained Agent In Action

I have recorded a video of the trained agent in action. To watch the video please click on the below image.

[![Trained Agent](https://img.youtube.com/vi/iLqFUZT3pVY/0.jpg)](https://www.youtube.com/watch?v=iLqFUZT3pVY)
