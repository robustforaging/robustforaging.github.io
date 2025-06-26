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
  - The task is adapted from a real neuroscience experiment in which **mice perform the same foraging task**. 

This setup enables comparison between biological and artificial agents under identical visual conditions.

## Download & Quick Start
Choose the build for your platform:

| Platform                    | Instruction       | Download Link                                                               |
| --------------------------- | ---------------- | --------------------------------------------------------------------------- |
| **Windows (GUI)**           | [Instruction](https://docs.google.com/document/d/13K5BHU-CeFdxnPgKUj9akWA_bw_Q4DFQ/edit?usp=sharing&ouid=110446495883463201050&rtpof=true&sd=true)      | [Windows v1.0](https://drive.google.com/drive/folders/12oXbrWm1nBfZup3pgCzRlkFjhB-7hD1r?usp=drive_link)      |
| **macOS (GUI)**             | [Instruction](https://docs.google.com/document/d/1QGGkKXfbF1gw_oYXV1auGjMaMyDUwiDP/edit?usp=sharing&ouid=110446495883463201050&rtpof=true&sd=true)      | [macOS v1.0](https://drive.google.com/drive/folders/1WaLZPkXFRx3afB3OZ2CO50Rk87ec3NEp?usp=sharing)           |
| **Linux (GUI)**             | [Instruction](https://docs.google.com/document/d/1nXrvHx16Cu2Tw1sbHPbiBPkwyJWWQPg2/edit?usp=sharing&ouid=110446495883463201050&rtpof=true&sd=true)      | [Linux v0.9](https://drive.google.com/drive/folders/1SMpbTGzxGUCc4GL60sazBvEk6AJGQOdo?usp=sharing)           |



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

For questions, updates, and discussion, please [Join the Discord](https://discord.gg/65NMfWaX)
You can also reach us via email at [robustforaging@gmail.com](mailto:robustforaging@gmail.com)
