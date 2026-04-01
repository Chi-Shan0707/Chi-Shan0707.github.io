---
title: "Learning in Artificial and Biological Systems- From In-ContextLearning Phase Transitions to Animal behavioral learning"
date: 2026-03-15
excerpt: "My Notes from Dr. Cui's Lecture "
tags:
  - AI
  - cogonition
---

## Artificial Learning
<p>
First, let's see AI.
<p>

<p>
Since Large models are large, so we construct a simple markov (rule) to generate random structured sequences, and then we uese a single two-layer transformer nerual network to learn the structure.
<p>

<p>
Experiments show 4 behaviours:
- Unigram Retrieval
- Bigram Retrieval
- Unigram Inference
- Bigram Inference
<p>

<!-- 
Unigram Retrieval（一元检索）：模型直接从预训练权重中提取单个状态的全局先验概率，忽略当前的上下文。
Bigram Retrieval（二元检索）：模型依靠记忆，输出预训练数据中固化的状态转移矩阵（固化的 $P(X_{t+1}|X_t)$）
Unigram Inference（一元上下文推断）：模型在当前的 Prompt 窗口内，动态统计各个 Token 出现的频率（Empirical Count），不考虑序列顺序。
Bigram Inference（二元上下文推断）：这是最高级的算法，也就是归纳头机制。模型像一个在线学习算法一样，在 Prompt 窗口内动态构建这个prompt是一个动态的长度吗  -->

<p>
Besides, thanks to the small model only with 5 parameters, we can easily to draw the picture.
And we can get:
- a cliff landscape
- a simple dynamical system
- a phase portrait about first-order phas transition from unigram generalization to memoriazation
<p>
<!-- 我们可以研究这种推动力是什么 -->

Summary 
1. 4 algorithms can be naturally implemented by in-context learning of Markov processes by a simple two-layer transformer architecture.
2. Abrupt learning can be explained by the cliff landscape predicted from our minimal models.
3. A scaling relation between the timing of abrupt learning and the context length is derived.
4. In  the finite task-diversity regime, we identfy two distinct phase trainsitions between memorization and generalization, determined by competition and model capacity, respectivley.
5. The generalization ability does not always scale up with model size.


## Biological Learning

<p>
Then let's pay attention to rats.
<p>

<p>
We can easily observe with sensors.<br>
We can easily conduct reinforcement-training( not learning lol)<br>
<p>

<p>
We use Moseq to decompose action into different small units,or attempts.
And we can cluster attempts into motifs.
<p>


There are a few conclusions:
- They study simple motif dynamics reduced from complicated motion trajectories
- They have task-dependent selection for specific behavioral motifs
- Abrupt improvement happens between day breaks

<p>
Take home message: biological motor learning operate through a select-and-refine strategy
rather than generate-from-scratch strategy
<P>


## Shared Principles of Artificial and Biological Learning


| Principle | AI Side | Biological Side |
| :--- | :--- | :--- |
| **1. Learning builds from compositional primitives** | High-level cognitive functions of large models emerge from the self-organization and combination of minimal underlying "computational modules" (especially induction heads), like cells and building blocks. | Rats' complex trial-and-error behaviors are constructed by splicing and combining basic discrete actions ("syllables") into fixed "motifs". They select and combine from an innate action repertoire, rather than creating from thin air. |
| **2. Learners extract structures from the environment** | Minimal networks can read context and spontaneously extract the "hidden transition rules" behind Markov sequences, completing the inference from unigram to bigram. | Rats in the experimental box, relying only on extremely sparse water-drop reward signals, can gradually explore and extract the hidden rules (i.e., the 1.5-second action template set by the system). |
| **3. Early experience strongly shapes later learning** | Data bias in the early stages of training (the key driving force H in the dynamic equation) plays a decisive role. Without it, the "awakening" speed of large models would slow down significantly, or even change the evolutionary trajectory. | The passing line (threshold) setting in the early tasks for rats is crucial. If the threshold is too high at the beginning, rats will never learn; if the early threshold is low, allowing them to grasp the trick before increasing the difficulty, their performance will keep improving. |
| **4. Learning often proceeds through abrupt transitions** | The prediction error rate during large model training will suddenly drop down a "loss cliff" after a long period of stagnation, resulting in an algorithmic "phase transition" (epiphany). | The action accuracy of rats usually does not progress at a uniform speed during same-day practice, but experiences sudden performance leaps the next day (after errors are repaired during offline states like sleep). |
