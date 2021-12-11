---
layout: default
title: Final Report 
---

# Project Summary:  [TODO]
  We implemented a game called CrossTheFireLine, similiar to the Dodge Ball; the agent should learn to avoid getting hit by the fireball from the Ghast as well as  to avoid stepping on the fire block. A ghast that can shoot fireballs will appear in the air and move randomly. When fireball falls to the ground, the stone will be set on fire and these blocks will convert into fire blocks. If the agent steps on the fire or get git by the fireball, it will receive the negative reward. Both our agent Steve and the Ghast's activity space will be limited inside the 60 x 60 area, surrounded by sand walls. Steve needs to observe his surroundings and avoid getting negative reward so that he can survive for longer time. 
  
  The output of the algorithm should be the list of continuous movements.
  
# Approach: [TODO]
In order to prevent the agent from walking aimlessly, we confine the agent and ghast to a three-dimensional space. Ghast will continuously shoot fireballs at the agent, and the agent can perform [continuous] actions to avoid the fireball.

Firstly,we decided to observe the coming of the Fireball from the end point of the Fireball using Matplotlib, using the function ax.quiver, with parameters(x,y,z,motionX,motionY, motionZ) can calculated the needed information, and the graph is showed by
![image](https://github.com/Chilly712/CrossTheFireLine_Minecraft/blob/main/docs/images/axquiver.png)

We first modified the observation space to ensure that the information of fire block location can be passed to the agent. Our first attempt was to create a new fireball observation space to store areas that will be in fire soon (after ghast shoot the fire ball). That is, when calling get_observation() method, the agent will receive two arrays. However, we later found that the agent's performance did not improve duringtraining, so we speculated that the agent might not be able to distinguish between the two arrays, original observation space and fire_ball observation space. Therefore, we re-design our code to incorporate the information of the fireball observation space into the original observation space using logical_or in NumPy. Finally, we applied the Proximal Policy Optimization (PPO) to train our agent.


To see how well the agent performs, we wrote the baseline for comparison. The baseline is allowing agent to only view the nearest block left, right, front, and back. We declare the empty list for storing the safe block and another list to store all moves in 4 different directions. If the left block is NOT occupied by the fire, the turn left command will be added to the safe_block list. Similarly, for all other 3 blocks applied the same rules. After the verification, we make agent randomly pick the command in the safe_block list, which means any command in the list will lead to the safe move. However, if 4 nearest blocks is full of fire, agent would have no choice but torandomly pick one command and execute it. We regard the baseline as a minimum standard; our agent must perform better than the baseline result, and has the basic consciousness not to step on the fire.


# Evaluation: 
  We want to see a situation where the agent can only make random choices at the beginning, then the agent will die quickly. However, as the number of training times increases, the agent knows what kind of action to preform to keep himself from dying.
  
 1. Survival Time Graph
  
 2. Reward Graph



# Reference: [TODO]
  Malmo project documentation and github page to set up the xml environment
  <br>
  http://microsoft.github.io/malmo/0.30.0/Schemas/MissionHandlers.html#SchemaPropertiesv
  <br>
  https://github.com/microsoft/malmo
  <br>
  PPO.PPOTrainer
  <br>
  Matplotlib for plotting fireball path
  <br>
  NumPy documentation
  <br>
  https://docs.ray.io/en/latest/rllib-env.html
  
