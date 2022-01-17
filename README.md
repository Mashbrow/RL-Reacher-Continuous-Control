# RL-Reacher-Continuous-Control

## Introduction

This project is part of the Udacity Nanodegree on Reinforcement Learning and aims at training a double-jointed arm to reach target locations.

Description of the environment:
- Reward: +0.1 for each time step that the agent's hand is in the goal location (The more the hand stay in the desired location the more reward it gets)
- Observation Space: 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm.
- Action Space : 4-dimensional space corresponding to torque applied on two joints (every number of each vector should be between -1 and 1).

The task is considered solved when the agent reaches an average score of +30 over 100 consecutives episodes.

## Installation 

Follow the instructions on this [repo](https://github.com/udacity/deep-reinforcement-learning#dependencies) to install all the dependencies Note that if you are running the code on Windows you might have trouble installing the box2d environnement you can solve this issue by using `pip install box2d` instead of `pip install gym[box2d]`.

Then follow the instructions on this [section](https://github.com/udacity/deep-reinforcement-learning/tree/master/p2_continuous-control).

## Method

Code was adapted from an implementation of DDPG ( that you can find on this [repo](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum) that I adapted so that it can achieve the task.

This project was less direct than the first one I made on RL. I started with the first environment containing only one agent but didn't get anything relevant even though I litteraly spent days tuning hyperparameters and changing model architecture. Training was at most unstable when the agent wasn't training anything. After getting a hard time with this first environment I decided to try the other one and tune it so that one agent was trained using the experiences from the 20 arms. 

Again I spent several days tuning hyperparameters and fixing bugs that prevented me from achieving this task (Those bugs were probably one of the causes of why I wasn't able to get any results in the first environment) before finally get an average score of =30.

Here are the things I changed and my insights on the environment:
- Inscreased model size so that more parameters were used for training for both Actor and Critic.
- Sharing the 20 arms experiences to train one agent, that is only one Actor and Critic model. It surely inscreased training by a factor of 20 comparing to the only one arm environment. It is something I will experiment later to understand why I did so bad with the first environment. 
- Tweaked hyperparameters, in particular the agent trains better by lowering the sigma of the noise, the learning rate of the model and the tau for the soft update.

## Future work

- Retry on the first environment to understand what lacked the first time.
- Implement other algorithm to achieve the task to compare with DDPG

## What contains this repository ?

- A notebook containing the code to train an agent to solve the task.
- A .py file containing the architecture of DDPG Agent.
- Two .pth files containing the weights of the Actor and the Critic models.
- A report describing the architecture and the hyperparameters used to solve the task aswell as my approach to solve the task.
