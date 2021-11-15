---
layout: default
title:  Status
---

# Project Summary: 
  We implemented a game called CrossTheFireLine, similiar to the Dodge Ball; the agent should learn to avoid getting hit by the fireball from the Ghast as well as  to avoid stepping on the fire block. A ghast that can shoot fireballs will appear in the air and move randomly. When fireball falls to the ground, the stone will be set on fire and these blocks will convert into fire blocks. If the agent steps on the fire or get git by the fireball, it will receive the negative reward. Both our agent Steve and the Ghast's activity space will be limited inside the 60 x 60 area, surrounded by sand walls. Steve needs to observe his surroundings and avoid getting negative reward so that he can survive for longer time. 
  
  The output of the algorithm should be the list of continuous movements.
  
# Approach: 

In order to prevent the agent from walking aimlessly, we confine the agent and ghast to a three-dimensional space. Ghast will continuously shoot fireballs at the agent, and the agent can perform continuous actions to avoid the fireball. Currently, we continued apply the Proximal Policy Optimization (PPO) to train our agent.

## Setup an Environment
![image](https://github.com/Chilly712/CrossTheFireLine_Minecraft/blob/main/env_image.jpg)

## Action
The Ghast can hit several blocks by launching single fireball, so if the agent only take discrete movement, its chances of avoiding the fireball are reduced. Hence, we believe the better choice is to let the agent have continuous movements .

## State
In order to make the agent gain a larger view, we expand the array size returned by get_observation to be (5x5).

## Reward
It is known that Ghast will launch a fireball at the position where the agent is located, and once the fireball hits the ground, it will ignite the stones on the floor and convert the stones into a fire block. We will get the 5x5 grid around the agent through get_observation() based on agent's location. Since the agent moves randomly during the training process, we use the coordinates of the agent to determine whether it is on the block hit by the fireball. If the agent is in the fire block, a negative reward is given. If the agent steps on the stone successfully, a positive reward will be given.

- Calculation method: 
take the position where ghast is scheduled to launch the fireball as the aim position; take the X position and Y position after the agent takes the action as the current position. If the aim position is included in the 5x5 grid observed by current position, we will update the corresponding block in current grid to fire. Therefore, the agent can repeatedly take the next action based on the latest situation.

By calculating the difference in the health value (Life) returned by each episode of the agent, we can determine whether the agent was hit by a fireball or stepped on the fireblock. If the Life decreases, it means that the agent has not taken a good action, so the negative reward will be given, and vice versa.

The agent’s initial life is 20, and the damage of single fireball is not that huge. Therefore, under certain conditions (for example, all the blocks around the agent are fireblock, and the agent has nowhere to go), the agent is bound to step on the fireblock. While the negative reward is given, we also obtain the survival time of the agent through the timeAlive atttribute in the observation, so we can use the time that the agent survives as the positive reward.


# Evaluation: 
  An important aspect of your project, as we mentioned in the beginning, is evaluating your project. Be clear and precise about describing the evaluation setup, for both quantitative and qualitative results. Present the results to convince the reader that you have a working implementation. Use plots, charts, tables, screenshots, figures, etc. as needed. I expect you will need at least a 1-2 paragraphs to describe each type of evaluation that you perform.

# Remaining Goals and Challenges:  
  So far, we can observe the Fireball path and avoid getting hit beforehead since it is an entity from <ObservationFromNearbyEntities> within a certain amount of LineSight. We might want to improve how we avoid the fireball. For example, making the agent Steve's vision more wide and open, changing the orientation more often. 
  We can also add the function of fire extinguishing, because a fireball can generate a lot of fire blocks, so sometimes it is difficult for the agent to cross the line of fire, if there is a fire extinguishing function will be more convenient for the agent not to receive harm

# Resources Used:   
  previous assignments
  
  Malmo project documentation
  
  PPO.PPOTrainer
