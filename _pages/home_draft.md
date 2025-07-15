---
layout: splash
title: "Robust Foraging Competition"
nav_exclude: true          # keeps it out of the menu (Just-the-Docs, Minimal Mistakes, etc.) :contentReference[oaicite:2]{index=2}
permalink: /home-draft/    # single, trailing-slash permalink
robots: noindex,nofollow   # stop search engines indexing it
sitemap: false             # keep it out of jekyll-sitemap.xml
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/banner-new.png
  actions:
    - label: "<i class='fas fa-download'></i> Install now (Windows)"
      url: "https://github.com/robustforaging/mouse_vs_ai_windows"
    - label: "<i class='fas fa-download'></i> Install now (macOS)"
      url: "https://github.com/robustforaging/mouse_vs_ai_macOS"
    - label: "<i class='fas fa-download'></i> Install now (Linux)"
      url: "https://github.com/robustforaging/mouse_vs_ai_linux"
excerpt: >
  Can your AI visually navigate better than a mouse?<br />
---

<style>
  .full-width-element {
    width: 100vw;
    position: relative;
    left: 50%;
    transform: translateX(-50%); /* Centers the element */
  }

  .page__title {
    color: #222831 !important;
    text-shadow: none !important;
  }

  .page__lead {
    color: #222831 !important;
    text-shadow: none !important;
  }

  .btn--light-outline {
    color: #222831 !important;
    border-color: #222831 !important;
    text-shadow: none !important;
  }

  .btn--light-outline:hover {
    color: #ffffff !important;
    background-color: #222831 !important;
    border-color: #222831 !important;
  }

  /* put this right after your existing styles */
  .competition-diagram,     /* the figure             */
  p {                       /* regular paragraphs     */
    margin-top: 2rem;       /* ↑ space above          */
    margin-bottom: 2rem;    /* ↓ space below          */
  }

  .mt-2 { margin-top: 1rem;  }
  .mt-4 { margin-top: 2rem;  }
  .mb-2 { margin-bottom: 1rem; }
  .mb-4 { margin-bottom: 2rem; }
</style>


Welcome to the Mouse vs AI: Robust Visual Foraging Competition @  **NeurIPS 2025 Competition Track**.

Mice robustly navigate in a range of conditions like fog, maybe more robustly than self-driving cars, which can struggle with out-of-distribution conditions. Build an AI agent that can outcompete a mouse!

<center>
<div class="full-width-element">
<video width="640" height="320" controls="controls" autoplay loop muted>
  <source src="/assets/images/tesla_fog_cut.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<video width="640" height="320" controls="controls" autoplay loop muted> -->
  <source src="/assets/images/example_video_mice_blur.mp4" type="video/mp4"> -->
  <Your browser does not support the video tag. -->
</video>
</div>
</center>

In this competition, we have generated a unique data set that includes hours of mice performing a visual navigation task in a detailed virtual reality (VR) environment (in Unity), under a range of perturbations to the visual stimuli (fog, etc.).
<ul>
  <li><strong>Track 1 — Visual Robustness:</strong>
      Build an AI agent that interfaces with the same VR game and try to
      outperform a mouse when faced with various visual perturbations.</li>

  <li><strong>Track 2 — Neural Alignment:</strong>
      We used two-photon imaging to record cortical activity while mice perform
      the task.  Predict those neural responses from your agent’s encoder
      activations—does it extract the same information?</li>
</ul>
    
##  Competition Overview

<figure class="competition-diagram">
  <img src="/assets/images/Figure_website.jpg"
       alt="Overview of the Mouse-vs-AI competition…">

  <figcaption class="fig-caption">
    <strong>Figure&nbsp;1.</strong> Overview of the <em>Mouse&nbsp;vs&nbsp;AI – Robust Visual Foraging Challenge</em>.
    <strong>(Left)</strong> Build an AI agent that plays the same VR foraging task as the mice.
    <strong>(Center)</strong> <u>Track 1</u> scores behavioural robustness: average and minimum success rate across one seen (fog) and three unseen perturbations.
    <strong>(Right)</strong> <u>Track 2</u> scores neural alignment: how well a linear readout from the agent’s visual-encoder activations predicts mouse V1 + HVA activity.
  </figcaption>
</figure>

  

### Motivation
Robust visual perception under real-world conditions remains a major bottleneck for AI agents: a modest shift in image statistics can collapse performance that was near-perfect during training.  
Biological vision, by contrast, is remarkably resilient. Mice trained for only a few hours under an unperturbed scene continue to solve the same visually guided foraging task when degradations such as fog are introduced, showing only a modest drop in success.

This competition transforms that gap into a quantitative benchmark. Participants train artificial agents to perform the **same** naturalistic foraging task, implemented in Unity, that we used for the mouse experiments. We provide two training conditions—a clean scene and a single illustrative perturbation (fog)—and agents may be trained on either or both. The resulting trained agent (visual encoder + policy) is the **sole submission for both tracks**.  
%

In **Track 1** we evaluate each submitted agent on the two provided conditions *plus* three held-out visual perturbations never encountered during training. Comparing architectures and training strategies under these unseen conditions reveals which approaches foster visual robustness approaching that of biological agents.  
While Track 1 focuses on behaviour, **Track 2** asks a complementary question: to what extent do those same visual encoders *spontaneously* align with mouse cortical activity? After training, we freeze each encoder’s weights, pass the mouse’s video through it to obtain hidden activations, and fit a linear regression that maps those activations to the spiking activity recorded from mouse V1 and higher visual areas while the mouse performed the task. Unlike previous alignment challenges—where networks are optimised directly for neural prediction —our encoders have never seen neural data, allowing us to measure *emergent* alignment.

The overarching goals are therefore (i) to identify architectural and training principles that support **visual robustness**, and (ii) to test whether those principles also yield **mouse-like internal representations**. By grounding evaluation in both behaviour and cortical activity, the challenge unifies reinforcement learning, robust computer vision, and systems neuroscience within a single task.


### Task Overview
Train an agent to navigate a naturalistic environment and reach a visually cued target within trialtime.
  - Training scene + one perturbation (fog) are provided, distance increases incrementally.
  - Final evaluation uses held‑out perturbations and starts each episode at max target distance.
  - The task is adapted from a real neuroscience experiment in which **mice perform the same foraging task**. 

This setup enables comparison between biological and artificial agents under identical visual conditions.

#### Track 1 — Visual Robustness*
   Evaluate how well your trained agent generalises to unseen visual perturbations.  
   *Metrics:* **Average Success Rate (ASR)**, **Minimum Success Rate (MSR)** across all provided and held-out conditions.

#### Track 2 — Neural Alignment
   Predict mouse visual-cortex activity from internal representations of your agent.  
   *Metrics:* **Mean Pearson correlation** between predicted and recorded neural responses.

Please note that the two tracks do not need to be submitted separately. All submissions will be evaluated in both tracks.


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




## Organizing Institutions




