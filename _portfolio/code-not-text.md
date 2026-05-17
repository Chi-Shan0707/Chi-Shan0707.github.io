---
title: "Code Correctness Is Not in the Text"
excerpt: "Probing the limits of Chain-of-Thought reasoning traces. A study on domain-dependent measurement invariance in LLMs."
collection: portfolio
header:
  teaser: "images/themes/code-not-text-teaser.png" # Placeholder or you can provide one
sidebar:
  - title: "Role"
    image: profile.png
    content: "Lead Researcher & Designer"
  - title: "Tech Stack"
    text: "Python, SVD, Logistic Regression, Transformer Lens"
---

<div style="text-align: justify; font-family: 'Inter', sans-serif;">

<p style="font-size: 1.2em; color: #555; font-style: italic; border-left: 4px solid #333; padding-left: 15px; margin-bottom: 30px;">
  "Correctness, however, lives in the runtime."
</p>

### The Core Inquiry
Can we judge the truth of a machine's conclusion simply by observing the 'shape' of its thoughts? This project investigates the limits of **surface-feature verification** in Large Language Models. By extracting over 30 hand-crafted metrics from reasoning trajectories—such as token certainty, trajectory continuity, and reflection counts—we attempted to build a "cheap" verifier that avoids expensive model-based judging.

### The Discovery: Measurement Invariance Failure
The results revealed a profound boundary in AI reasoning:
*   **Math (AUROC 0.982):** Reasoning correctness is highly visible. Truth manifests as linear, convergent paths.
*   **Code (AUROC 0.407):** Correctness is invisible to surface features. The textual 'prose' of a coding solution often masks logical failures that only emerge during execution.

<div style="background: #f9f9f9; padding: 20px; border-radius: 8px; margin: 20px 0; border: 1px solid #eee;">
  <strong>Key Insight:</strong> Code reasoning is a "knot" problem. Linear text is a poor representation of non-linear state changes, loops, and branching logic. Code correctness exists in the <em>runtime</em>, not the <em>text</em>.
</div>

### Features of the Study
*   **Behavioral Probing:** Developed a "Cheap Feature Family" stack (StandardScaler → TruncatedSVD → LogisticRegression).
*   **Five Convergent Checks:** Validated findings across SSL, MLP, and "De-knotting" experiments.
*   **Aesthetic Visualization:** Designed a high-signal dashboard to contrast "Clean, Convergent" Math CoT with "Conditional Maze" Coding CoT.

---

<div style="text-align: center; margin-top: 40px;">
  <a href="https://chi-shan0707.github.io/code-not-text/demo/" class="btn btn--primary btn--large" style="text-decoration: none; font-weight: bold;">Explore the Interactive Demo</a>
</div>

</div>
