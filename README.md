# Eco-Driving Agent using Deep Reinforcement Learning

This project is my exploration into applying Deep Reinforcement Learning to a key challenge in modern automotive engineering: energy-efficient vehicle control. I developed an intelligent agent that learns to drive a simulated vehicle along a target speed profile, with the primary goal of minimizing energy consumption by adopting a smooth and anticipatory driving style.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Core Methodology](#core-methodology)
- [Results: Generalization to Real-World Data](#results-generalization-to-real-world-data)
- [Repository Structure](#repository-structure)
- [Setup and Installation](#setup-and-installation)
- [How to Run](#how-to-run)
- [Future Work](#future-work)
- [License](#license)

## Project Overview

The goal of this project was to move beyond simple vehicle control and create a policy that is intelligent and efficient. For any vehicle, but especially electric ones, optimizing energy usage is critical. I tackled this challenge by training a Reinforcement Learning agent to find an optimal balance between accurately following a speed command and minimizing energy use. The agent achieves this by learning when to accelerate, when to brake, and, most importantly, when to coast to conserve momentum, mimicking the behavior of an expert human driver.

## Key Features

- **Custom Reinforcement Learning Environment:** I built a custom environment from scratch using `gymnasium`, the industry-standard library for RL development.
- **Advanced Reward Shaping:** The agent's learning process is guided by a sophisticated reward function I designed to penalize jerky actions and explicitly reward energy-efficient coasting.
- **Deep Q-Network (DQN) Agent:** The control policy is learned using a DQN agent, implemented with the robust `stable-baselines3` library.
- **Training on Standardized Data:** The agent is trained on the Worldwide Harmonised Light Vehicle Test Procedure (WLTP), a global industry benchmark for vehicle testing.
- **Validation on Real-World Data:** I tested the final agent's ability to generalize on a separate, unseen real-world driving dataset, proving it learned a transferable skill rather than just memorizing the training data.

## Core Methodology

I followed an iterative development process to achieve the final result:

1.  **Initial Prototype (V1):** My first agent was rewarded only for tracking the target speed. This led to a policy that, while functional, was highly inefficient and exhibited "control chattering"—rapidly oscillating between full acceleration and braking.

2.  **Reward Shaping (V2):** To solve this, I engineered a more intelligent environment to teach the agent *how* to drive efficiently.
    - A **jerk penalty** was added to discourage rapid changes in action.
    - A **coasting bonus** was introduced to explicitly incentivize the most energy-efficient action.
    - The agent's observation space was expanded to include a "lookahead" at future speeds, enabling it to make anticipatory decisions.

3.  **Training and Validation:** I trained the final agent exclusively on the WLTP cycle. I then measured its performance by evaluating it on both the WLTP cycle and a completely unseen real-world driving cycle to test its generalization capabilities.

## Results: Generalization to Real-World Data

The key success of this project is its demonstration of generalization. After training on the standardized WLTP cycle, the agent was able to apply its learned eco-driving strategy to a novel, real-world drive cycle without any retraining.

My evaluation showed that the agent maintained its smooth, coast-centric strategy in this new environment. This confirmed that the agent learned a robust and transferable strategy for energy-efficient driving, which was the central goal of the project.
