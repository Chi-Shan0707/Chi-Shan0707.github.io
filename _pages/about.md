---
permalink: /
title: "Do interesting things"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<div style="text-align:right; margin-bottom:0.8rem;">
   <a href="{{ '/zh/' | relative_url }}" style="font-size:0.9rem;">中文</a>
</div>

## Basic Info

***
- China - Shanghai
- GitHub: [Chi-Shan0707](https://github.com/Chi-Shan0707)


I am currently an undergraduate student at the School of Mathematical Sciences, Fudan University, pursuing a double degree in Information and Computing Science and Artificial Intelligence.<br>
At the same time, I have been actively self-studying interesting topics across computer science.<br>
I am exploring the intersection I truly want to work on and study.<br>
I hope to contribute to making society better.<br>


## My featured works

I enjoy building small but complete research systems, writing technical notes, and turning vague ideas into runnable artifacts.


***


### [SVDomain](https://github.com/Chi-Shan0707/SVDomain)

**I propose SVDomain : a domain-conditioned low-rank framework for chain-of-thought analysis.**

<details>
<summary>Overview</summary>

SVDomain is a domain-conditioned low-rank framework that builds feature views from token-level confidence and uncertainty statistics, trajectory summaries, and availability indicators, and learns a shared latent basis with a lightweight linear readout.

- Canonical pipeline: StandardScaler → TruncatedSVD → LogisticRegression
- Downstream tasks: EarlyStop, Best-of-N bridging, RL checkpoint ranking.
- Focus: when low-rank structure becomes predictive, how bases transfer across anchors, and how the same low-rank object can support both prediction and explanation.

This repository contains a paper-style writeup and code to reproduce experiments and analyses.

</details>

### [TinyLoRA-GRPO-Coder](https://github.com/Chi-Shan0707/TinyLoRA-GRPO-Coder)

**Low-parameter adaptation and reinforcement learning for code generation.**

<details>
<summary>Overview</summary>

An independent open-source reimplementation and adaptation of TinyLoRA + GRPO from [Learning to Reason in 13 Parameters](https://arxiv.org/abs/2602.04118), migrated from math reasoning to verifiable competitive-programming code generation. Built on Qwen2.5-Coder-3B with only a tiny number of shared trainable parameters, the project uses real compile-and-run rewards rather than static heuristics. I developed the full pipeline end to end, including data processing, training, multi-GPU setup, reward design, evaluation, and validation, which significantly strengthened my ability to turn a paper into a working research system.

</details>

## My repos

- The following projects were primarily completed independently, with AI used only as an auxiliary tool where appropriate. These works were not conducted under a laboratory or research group; rather, they reflect my self-directed exploration, sustained learning, and independent implementation outside a formal research environment.

<details>
<summary><a href="https://github.com/Chi-Shan0707/KaggleCompetitions" target="_blank" rel="noopener">KaggleCompetitions</a></summary>

<p>Participated in several <strong>Kaggle competitions</strong> (see repo: <a href="https://github.com/Chi-Shan0707/KaggleCompetitions" target="_blank" rel="noopener">KaggleCompetitions</a>), gaining broad exposure to and practical experience with various machine learning tools.</p>

</details>

<details>
<summary><a href="https://github.com/Chi-Shan0707/Hone-My-C-Plus-Plus-" target="_blank" rel="noopener">Hone My C Plus Plus</a></summary>

<p>Explorations of <strong>Advanced Algorithms</strong> and <strong>Modern C++</strong> can be found in <a href="https://github.com/Chi-Shan0707/Hone-My-C-Plus-Plus-" target="_blank" rel="noopener">Hone My C Plus Plus</a>.</p>

</details>

<details>
<summary><a href="https://github.com/Chi-Shan0707/microgpt.cpp" target="_blank" rel="noopener">microgpt.cpp</a></summary>

<p>A simple <code>microgpt.cpp</code> in ~300 lines (repo: <a href="https://github.com/Chi-Shan0707/microgpt.cpp" target="_blank" rel="noopener">microgpt.cpp</a>).</p>

</details>

<details>
<summary><a href="https://github.com/Chi-Shan0707/Baseball" target="_blank" rel="noopener">Baseball</a></summary>

<p>A <strong>Strike/Ball Classification Model</strong> using CNN + ResNet18 for baseball pitch analysis (repo: <a href="https://github.com/Chi-Shan0707/Baseball" target="_blank" rel="noopener">Baseball</a>).</p>

</details>

<details>
<summary><a href="https://github.com/Chi-Shan0707/Sample-Java" target="_blank" rel="noopener">Sample Java</a></summary>

<p>The essence of <strong>Randomized Algorithms</strong>—the "Art of Sampling"—and my first taste of Java. Repo: <a href="https://github.com/Chi-Shan0707/Sample-Java" target="_blank" rel="noopener">Sample Java</a>.</p>

</details>

<details>
<summary>DeepLearning / GenerativeModel / ReinforcementLearning</summary>

<p>These three repositories serve as <strong>learning records</strong> covering theory → implementation:</p>
<ul>
   <li><a href="https://github.com/Chi-Shan0707/DeepLearning" target="_blank" rel="noopener">DeepLearning</a></li>
   <li><a href="https://github.com/Chi-Shan0707/GenerativeModel" target="_blank" rel="noopener">GenerativeModel</a></li>
   <li><a href="https://github.com/Chi-Shan0707/ReinforcementLearning" target="_blank" rel="noopener">ReinforcementLearning</a></li>
</ul>

</details>

 - The following project was completed in collaboration with others.

<details>
<summary><a href="https://github.com/Chi-Shan0707/NAD_Next" target="_blank" rel="noopener">NAD Next</a></summary>

<p>A collaborative framework for analyzing large-language-model neuron activations and reasoning processes. The project covers activation-cache construction, selector evaluation, token-level statistics, and visualization. Our goal is to compare different runs on the same problem via CoT-, activation-, and ensemble-based signals, and estimate which run is more likely to be correct or incorrect.</p>

<p>My primary contribution: algorithm construction and method design.</p>

> Note: This project is currently a work in progress (WIP). Due to practical constraints, some content cannot be open-sourced on GitHub immediately; therefore, the current public repository is not yet complete. We will continue to add materials and update toward a more complete release as conditions permit.

</details>

***


## Service and Community Involvement

Beyond my personal projects, I also contribute to community-oriented open-source work.

   1. [github-unflag-playbook-cn](https://github.com/Chi-Shan0707/github-unflag-playbook-cn) <br>
      A Chinese playbook documenting GitHub account flagging/recovery experiences, appeal processes, and case archives for mainland China developers.
   2. [FDUGuideBook/nav-site](https://github.com/FDUGuideBook/nav-site) <br>
      Contribute to this navigation site for the Fudan community continuously.

## Tech stack and tools

| Domain         | Skills                                                                 |
|----------------|------------------------------------------------------------------------|
| **Language**    | <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/python/python-original.svg" width="20"> Python &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/nodejs/nodejs-original.svg" width="20"> Node.js &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/cplusplus/cplusplus-original.svg" width="20"> C++ &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/c/c-original.svg" width="20"> C &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/java/java-original.svg" width="20"> Java &nbsp; <img src="/icons/lean4.jpg" width="20"> Lean 4 &nbsp;  ε-N language, ε-δ language |
| **IDE**        | <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/vscode/vscode-original.svg" width="20"> VS Code &nbsp;  📕Draftbooks|
| **OS**         | <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/windows8/windows8-original.svg" width="20"> Windows &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/linux/linux-original.svg" width="20"> Linux |
| **Other**      | <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/markdown/markdown-original.svg" width="20"> Markdown &nbsp; <img src="https://cdn.jsdelivr.net/npm/devicon@2.15.1/icons/latex/latex-original.svg" width="20"> LaTeX &nbsp; <img src="/icons/redstone.jpg" width="20"> Redstone |





***

## Education

<!-- - <img src="/icons/fdfzlogo.jpg" alt="FDFZ" width="64" style="vertical-align:middle; margin-right:8px;" /> 复旦大学附属中学 — [官网](https://www.fdfz.cn/)
- <img src="/icons/fudanlogo.png" alt="Fudan Math" width="64" style="vertical-align:middle; margin-right:8px;" /> 复旦大学数学科学学院 — [官网](https://math.fudan.edu.cn/) -->

School of Mathematical Sciences, Fudan University


*When clouds gather, the mountain grows lovelier still; when they part, it stands like a painting.*<br>
*Clouds lend it shadow and light, and give shape to its height.*<br>
---
