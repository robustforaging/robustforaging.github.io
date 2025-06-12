---
layout: default
title: Home
---

# Robust Visual Foraging Challenge @ NeurIPS 2025

> **Announcement - Public Beta v0.9:**  
> Upcoming v1.0 (planned – 1 July 2025) will add:
> 1. Standalone Python API – train with any RL framework (PyTorch, TensorFlow, JAX) without Unity ML-Agents
> 2. Headless Linux builds optimised for SLURM / Kubernetes clusters


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
  - 
The task is adapted from a real neuroscience experiment in which **mice perform the same foraging task**. 
This setup enables comparison between biological and artificial agents under identical visual conditions.


## Quick Start

  ### 1 · Download the environment [MouseVsAI_Windows_v0.9.zip](https://drive.google.com/file/d/1S7KtiVVI5LaxVFGQlHjV0A1DzFGyklYo) (≈ 9 GB)
  
  ---
  
  ### 2 · Train your first agent
  
  Follow the **[Training Guide](/training_guide)**
  
  ---
  
  ### 3 · Submit your model
  
  Package your trained models and follow the **[Submission Guide](/submission_guide)** to upload to the leaderboard.


## Competition Tracks

### Track 1: Visual Robustness
  Evaluate how well your trained agent generalizes to unseen visual perturbations.  
  - **Metrics**: Average Success Rate (ASR), Minimum Success Rate (MSR) across all provided and held-out conditons
  
### Track 2: Neural Alignment (optional)
  Predict mouse visual cortex activity from internal representations of your agent.  
  - **Metrics**: Mean Pearson correlation between predicted and recorded neural responses


## Communication

For questions, updates, and discussion, please join our official Discord:

👉 [Join the Discord](https://discord.gg/65NMfWaX)

You can also reach us via email at [robustforaging@gmail.com](mailto:robustforaging@gmail.com)


## 🗓️ Timeline

| Date             | Milestone                        |
|------------------|----------------------------------|
| June 11, 2025    | Starter kit released             |
| July 1, 2025     | Competition begins               |
| Nov 1, 2025      | Final submission deadline        |
| Nov 15, 2025     | Evaluation + winners announced   |
| Dec 2025         | Results at NeurIPS 2025          |
