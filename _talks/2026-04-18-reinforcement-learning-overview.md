---
title: "A Quick Overview of Reinforcement Learning (RL)"
collection: talks
type: "Talk"
permalink: /talks/2026-04-18-reinforcement-learning-overview
venue: "Fudan University (internal seminar)"
date: 2026-04-18
location: "Shanghai, China"
---


Abstract<br>
This seminar serves as a theoretical prerequisite for understanding modern Large Language Model (LLM) reinforcement learning alignment techniques, such as GRPO and DAPO. Rather than focusing on the heavy engineering pipelines of RLHF, this talk constructs a rigorous, uninterrupted mathematical narrative.<br>

We begin with the minimal decision-making loop of Multi-Armed Bandits and naturally progress through Contextual Bandits, Markov Decision Processes (MDPs), and Policy Gradients, before culminating in Proximal Policy Optimization (PPO). The primary objective is to equip attendees with a clear intuition and mathematical understanding of core RL mechanisms—such as the log-derivative trick, advantage estimation, and ratio clipping—enabling them to seamlessly parse the objective functions of state-of-the-art LLM alignment algorithms.<br>

Key Topics Covered
- The Minimal Decision Loop: Multi-Armed Bandits and Contextual Bandits.
- Credit Assignment: MDPs, Trajectories, and Value Functions.
- Value Estimation: Monte Carlo (MC) vs. Temporal Difference (TD) learning.
- Direct Policy Optimization: Policy Gradients (REINFORCE) and the log-derivative trick.
- Variance Reduction: Baselines, Advantage functions, Actor-Critic architectures, and Generalized Advantage Estimation (GAE).
- Stable Policy Updates: Proximal Policy Optimization (PPO) and importance ratio clipping.
- Bridging the Gap: Why Q-learning/DQN is computationally prohibitive for LLMs, and how PPO lays the groundwork for GRPO/DAPO.




You can get a pdf here.