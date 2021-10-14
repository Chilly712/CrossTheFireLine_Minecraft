---
layout: default
title:  Proposal
---

## Summary of the Project

We will be implementing a game inside Minecraft, similiar to the Doodle Game, jumping from one platform to another. 
The main goal for our AI is to reach the platform as high as possible(y-coordinate) in the given time interval (120s). 
There will be different types of blocks, normal block(reward++), diamond block(reward++), air block(player die, reward--)

So far, there are 2 methods to create input under consideration. We are still considering which method to apply in the implementation.
The first one is generating the entire route panorama(third person perspective), while the other one is generating platforms within the screen shoot (the first person perspective). 

The output of our algorithm is a list of action that our AI player will be taken.

## AI/ML Algorithm
Q-learning, Deep Reinforcement Learning Algorithm

python3 pyTorch/Tensorflow, might be using Neural Network, CNN/RNN/LSTM

openCV / ImageNet


## Evaluation Plan

# Evaluate the successfule of the project:

  Matrics:
  
  -- Rate: diamond blocks that the agent reached / diamond blocks the agent passed
  
  -- Height: hight that our agent reached (y-coordinate)

  Baseline:
  
  -- hightest platform that agent can reach without considering getting extra rewards

  Data to eval:
  
  -- life loss
  
  -- reward gain
  

# Verfy the project works:

  Sanity check: we need to make sure the agent can at least jump to the up level platform.

  Q-learning Loss function 

  a diagram showing the score per life as we train AI

  Cumulative Rewards diagram



## Appoitment with the Instructor
10.19 2:45PM
