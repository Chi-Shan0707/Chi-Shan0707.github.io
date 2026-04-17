---
title: "From Bandits to PPO: RL Prerequisite Seminar"
collection: talks
type: "Talk"
permalink: /talks/2026-04-18-reinforcement-learning-overview
venue: "Fudan University (internal seminar)"
date: 2026-04-18
location: "Shanghai, China"
excerpt: "A one-hour mathematical bridge from bandits to PPO, designed as preparation for GRPO/DAPO discussions."
pdf_url: "/files/From%20Bandits%20to%20PPO.pdf"
---

This page is the seminar detail page for "From Bandits to PPO".

The PDF notes are the complete written version of this seminar. They include the full formulas, derivations, and algorithm summaries that are only briefly mentioned on this page.

The content follows a single line: Bandits -> MDPs -> MC/TD -> policy gradient -> GAE -> PPO. The goal is to keep the concepts connected, so readers can see where each method comes from and why PPO is the endpoint of this prerequisite talk.

[Read the Full LaTeX Notes (PDF)](/files/From%20Bandits%20to%20PPO.pdf){: .btn .btn--primary }

If you want a quick reading path, focus on these four points:

1. The basic map: what is learned (value vs. policy) and how the learning signal is estimated (MC vs. TD).
2. Variance reduction: baseline, advantage, actor-critic, and GAE.
3. Update stability: why plain policy gradient is unstable and how PPO clipping helps.
4. Handoff to the next topic: why PPO is a natural stopping point before GRPO/DAPO.

## Seminar Snapshot

| Item | Detail |
|---|---|
| Theme | Mathematical path from bandits to PPO |
| Positioning | Prerequisite for PPO-family LLM post-training methods (GRPO/DAPO) |
| Duration | 1 hour |
| Audience | Students with basic probability and linear algebra |
| Output | Conceptual map + formulas needed for next seminar |

## Seminar At A Glance

- Goal: understand why modern policy optimization naturally leads to actor-critic, GAE, and PPO
- Focus: theory and intuition first, engineering details later

## Simple Outline

1. Bandits and contextual bandits
2. MDPs, trajectories, and value functions
3. Monte Carlo vs. Temporal Difference (TD)
4. Tabular control: MC iteration, SARSA, Q-learning
5. Function approximation fork: DQN vs. policy parameterization
6. Policy gradient and REINFORCE
7. Baselines, advantage, actor-critic, and GAE
8. PPO clipping objective and practical training loop

## Key Mathematical Threads

- Learning object: value function vs. policy
- Learning signal: Monte Carlo returns vs. TD bootstrapping
- Variance control: baseline subtraction and advantage estimation
- Stability: importance ratio clipping in PPO

## Why This Stop Point Matters

PPO is the right endpoint for this seminar because it gives all the conceptual ingredients needed for understanding GRPO-like variants: policy gradient objective, advantage estimation, and controlled policy updates.

## Detailed Notes

For full derivations, proofs, and algorithm boxes, see the complete note:

- [From Bandits to PPO (PDF)](/files/From%20Bandits%20to%20PPO.pdf)