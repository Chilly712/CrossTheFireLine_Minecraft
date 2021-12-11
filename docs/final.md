---
layout: default
title: Final Report 
---

# Project Summary:  [TODO]
  We implemented a game called CrossTheFireLine, similiar to the Dodge Ball; the agent should learn to avoid getting hit by the fireball from the Ghast as well as  to avoid stepping on the fire block. A ghast that can shoot fireballs will appear in the air and move randomly. When fireball falls to the ground, the stone will be set on fire and these blocks will convert into fire blocks. If the agent steps on the fire or get git by the fireball, it will receive the negative reward. Both our agent Steve and the Ghast's activity space will be limited inside the 60 x 60 area, surrounded by sand walls. Steve needs to observe his surroundings and avoid getting negative reward so that he can survive for longer time. 
  
  The output of the algorithm should be the list of continuous movements.
  
# Approach: [TODO]



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
  
