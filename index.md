---
layout: default
title: Home
---

# Robust Visual Foraging Challenge @ NeurIPS 2025

<video width="480" height="320" controls="controls">
  <source src="/figures/example_video.mp4" type="video/mp4">
</video>

Welcome to the official competition page for the **Mouse vs AI: Robust Visual Foraging Challenge**, part of the NeurIPS 2025 Competition Track.

Biological agents like mice can robustly perform visually guided tasks in complex environments — even under fog, blur, or visual noise. Can your agent do the same?


## Goal

The goal of this competition is to benchmark and improve the robustness of artificial agents in biologically inspired visual tasks. Specifically, we aim to:

- Evaluate generalization under unseen visual perturbations
- Compare artificial agent performance to real mouse behavior under identical conditions
- Provide a biologically grounded benchmark for embodied visual AI systems
- Offer an neural alignment track to assess how well models align with cortical representations


## Task Overview
Train an agent to navigate a naturalistic environment and reach a visually cued target within trialtime.
  - Training scene + one perturbation (fog) are provided, distance increases incrementally.
  - Final evaluation uses held‑out perturbations and starts each episode at max target distance.
  - The task is adapted from a real neuroscience experiment in which **mice perform the same foraging task**. 

This setup enables comparison between biological and artificial agents under identical visual conditions.

## Download & Quick Start
Choose the build for your platform:

| Platform                    | Dowload Link                                                              |
| --------------------------- | --------------------------------------------------------------------------|
| **Windows (GUI)**           | [Windows v1.0](https://github.com/robustforaging/mouse_vs_ai_windows)     |
| **macOS (GUI)**             | [macOS v1.0](https://github.com/robustforaging/mouse_vs_ai_macOS)         |
| **Linux (GUI)**             | [Linux v1.0](https://github.com/robustforaging/mouse_vs_ai_linux)         |



1. **Download the environment**
2. **Install dependencies**
3. **Train your first agent** 
4. **Submit your model** — Package your trained models and follow the **[Submission Guide](submission_guide)**.


## Competition Tracks

1. **Track 1 — Visual Robustness**  
   Evaluate how well your trained agent generalises to unseen visual perturbations.  
   *Metrics:* **Average Success Rate (ASR)**, **Minimum Success Rate (MSR)** across all provided and held-out conditions.

2. **Track 2 — Neural Alignment** 
   Predict mouse visual-cortex activity from internal representations of your agent.  
   *Metrics:* **Mean Pearson correlation** between predicted and recorded neural responses.

Please note that the two tracks do not need to be submitted separately. All submissions will be evaluated in both tracks.

##  Timeline

| Date             | Milestone                        |
|------------------|----------------------------------|
| June 11, 2025    | Starter kit released             |
| July 1, 2025     | Competition officially begins    |
| Nov 1, 2025      | Final submission deadline        |
| Nov 15, 2025     | Evaluation + winners announced   |
| Dec 2025         | Results at NeurIPS 2025          |


## Communication

For questions, updates, and discussion, please [Join the Discord](https://discord.gg/7mJPh5QMB7)
You can also reach us via email at [robustforaging@gmail.com](mailto:robustforaging@gmail.com)
