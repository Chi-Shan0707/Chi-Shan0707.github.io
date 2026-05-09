---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

[**View PDF version**]({{ base_path }}/files/Yuhan_Chi_CV.pdf)

Profile
======
* First-year undergraduate at **Fudan University** (School of Mathematical Sciences), pursuing a double degree in **Information and Computing Science** and **Artificial Intelligence**.
* GPA: **3.96/4.00** (most recent semester); ranked **10th (top 5%)** in cohort.
* Research focus: mathematical foundations of intelligence, entrustable sequential decision-making, and reinforcement learning with world models.

Education
======
* **Fudan University**, Shanghai, China
  * **B.S. Candidate** in Information and Computing Science & Artificial Intelligence (Double Degree), School of Mathematical Sciences
  * **Sep. 2025 -- Present**
  * GPA: **3.96/4.00** (most recent semester)
  * Rank: **10th (top 5%)** in cohort

Research Interests
======
* **Mathematical Foundations of Intelligence**: grounding AI trust in formal mathematical terms rather than empirical benchmarks
* **Entrustable Sequential Decision-Making**: building agents that are mathematically verifiable and know when to act, defer, or bear consequences
* **Reinforcement Learning & World Models**: RL as a language for trust, uncertainty, and structured interaction with environments


Selected Open-Source Projects
======
* **[code-not-text](https://github.com/chi-shan0707/code-not-text)** — [Interactive Demo](https://chi-shan0707.github.io/code-not-text/demo)
  * Paper-level research on cross-domain limits of hand-crafted CoT-surface features for predicting solution correctness from reasoning traces
  * Evaluated on DeepSeek-R1-0528-Qwen3-8B across math, science, and coding; strong in math (AoA 0.958), below-chance in coding (AoA 0.434)
  * Five independent checks (probes, feature sweep, MLPs, SSL, de-knotting) all converge to the same coding ceiling, ruling out capacity, engineering, scarcity, and noise — code correctness is not in the text
  * Argued that CoT traces are not entrustable correctness instruments: they signal reasoning failure in math but only text fluency in coding, making execution feedback essential for verifiable agents
  * Interactive demo at [chi-shan0707.github.io/code-not-text/demo](https://chi-shan0707.github.io/code-not-text/demo)

* **[TinyLoRA-GRPO-Coder](https://github.com/Chi-Shan0707/TinyLoRA-GRPO-Coder)**
  * Independent reimplementation and adaptation of TinyLoRA + GRPO from *Learning to Reason in 13 Parameters*
  * Migrated the method from math reasoning to verifiable competitive-programming code generation on Qwen2.5-Coder-3B
  * Trained with a minimal number of shared trainable parameters; replaced static heuristics with real compile-and-run rewards
  * Built the full pipeline end to end: data processing, training, multi-GPU setup, reward design, evaluation, and validation

* **[microgpt.cpp](https://github.com/Chi-Shan0707/microgpt.cpp)**
  * Minimal GPT implementation from first principles in C++, built to understand model internals without relying on high-level frameworks


Skills
======
* **Programming:** Python, C++, C, Java, Node.js, Lean 4
* **ML/AI:** PyTorch, deep learning, LLM fine-tuning, reinforcement learning, computer vision
* **Tools:** Git, GitHub, Linux, LaTeX, Markdown, VS Code
* **Other:** Mathematical proof writing, technical writing, self-directed learning, competitive programming



Additional Information
======
* Maintains **[github-unflag-playbook-cn](https://chi-shan0707.github.io/github-unflag-playbook-cn)**, a Chinese playbook documenting GitHub account flagging, recovery cases, and appeal workflows
* Contributor to **[FDUGuideBook/nav-site](https://github.com/FDUGuideBook/nav-site)**, a Fudan community site
* Personal website: [chi-shan0707.github.io](https://chi-shan0707.github.io/)
* GitHub: [Chi-Shan0707](https://github.com/Chi-Shan0707)
* Actively self-studying mathematics, algorithms, and AI beyond formal coursework, with ongoing work documented in public repositories
