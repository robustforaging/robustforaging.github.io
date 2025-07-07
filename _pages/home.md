---
layout: splash
permalink: /
hidden: true
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/mouse-running-task-raw.png
  actions:
    - label: "<i class='fas fa-download'></i> Install now (Windows)"
            #url: [download](#download-&-quick-start)
    - label: "<i class='fas fa-download'></i> Install now (macOS)"
            #url: [download](#download-&-quick-start)
    - label: "<i class='fas fa-download'></i> Install now (Linux)"
            #url: [download](#download-&-quick-start)
            
excerpt: >
  A competition pitting an ai model against visual tasks a mouse can solve in fog, rain, etc.<br />
feature_row:
  - image_path: /assets/images/mouse-fighting_banner2.png
    alt: "submission"
    title: "Submission Guide"
    excerpt: "Pretty much almost everything you need to submit your ai model in this competition."
    url: "/submission-guide/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/mouse-fighting-raw.png
    alt: "training"
    title: "Training Guide"
    excerpt: "Hit the gym and get that ai model built like arnold."
    url: "/training-guide/"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/mouse-running-task-banner2.png
    alt: "organizers"
    title: "Amazing Organizers"
    excerpt: "Meet the lovely people that made this competition possible!"
    url: "/organizers"
    btn_class: "btn--primary"
    btn_label: "Learn more"      
---

{% include feature_row %}


# Robust Visual Foraging Challenge @ NeurIPS 2025


Welcome to the official competition page for the **Mouse vs AI: Robust Visual Foraging Challenge**, part of the NeurIPS 2025 Competition Track.

Biological agents like mice can robustly perform visually guided tasks in complex environments — even under fog, blur, or visual noise. Can your agent do the same?

<center>
<video width="640" height="320" controls="controls">
  <source src="/assets/images/example_video.mp4" type="video/mp4">
</video>
</center>

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
| July 1, 2025     | Starter kit released             |
| July 15, 2025    | Competition officially begins    |
| Nov 1, 2025      | Final submission deadline        |
| Nov 15, 2025     | Evaluation + winners announced   |
| Dec 2025         | Results at NeurIPS 2025          |


## Communication

For questions, updates, and discussion, please [Join the Discord](https://discord.gg/7mJPh5QMB7)
You can also reach us via email at [robustforaging@gmail.com](mailto:robustforaging@gmail.com)
