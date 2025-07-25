---
layout: splash
title: "Robust Foraging Competition"
nav_exclude: true          # keeps it out of the menu (Just-the-Docs, Minimal Mistakes, etc.) :contentReference[oaicite:2]{index=2}
permalink: /    # single, trailing-slash permalink
mathjax: true          # ← add this line
robots: noindex,nofollow   # stop search engines indexing it
sitemap: false             # keep it out of jekyll-sitemap.xml
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/mouse-fighting-raw3.png
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
  /* Enhanced styling for better visibility */
  .page__title {
    font-size: 3.5rem !important;
    font-weight: 700 !important;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7) !important;
    margin-bottom: 1rem !important;
  }

  .page__lead {
    font-size: 1.4rem !important;
    font-weight: 500 !important;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.6) !important;
    margin-bottom: 2rem !important;
  }

  .btn--light-outline {
    font-size: 1.1rem !important;
    font-weight: 600 !important;
    padding: 0.8rem 1.5rem !important;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5) !important;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3) !important;
    border-width: 2px !important;
  }

  .btn--light-outline:hover {
    color: #ffffff !important;
    background-color: #222831 !important;
    border-color: #222831 !important;
    transform: translateY(-2px) !important;
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.4) !important;
  }

  /* put this right after your existing styles */
  .competition-diagram,     /* the figure             */
  p {                       /* regular paragraphs     */
    margin-top: 2rem;       /* ↑ space above          */
    margin-bottom: 2rem;    /* ↓ space below          */
  }
  blockquote.track {
    border-left: none;      /* removes the bar */
    margin-left: 1.5rem;    /* keep the indent */
    padding-left: 0;        /* optional: flush text */
  }
  
  .math-center { text-align: center; }
  .mt-2 { margin-top: 1rem;  }
  .mt-4 { margin-top: 2rem;  }
  .mb-2 { margin-bottom: 1rem; }
  .mb-4 { margin-bottom: 2rem; }

  video {
  max-width: 680px;
  margin: 0 10px; /* adds 10px margin on left and right */
  }

  /* Hero background image scaling controls */
  .page__hero--overlay {
    background-size: cover !important;
    background-position: center !important;
    background-repeat: no-repeat !important;
    min-height: 400px; /* Ensure minimum height for the hero section */
  }

  /* Add blur effect to background image */
  .page__hero--overlay::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: inherit;
    background-size: inherit;
    background-position: inherit;
    background-repeat: inherit;
    filter: blur(5px);
    z-index: -1;
  }

  /* Ensure content appears above the blurred background */
  .page__hero--overlay .wrapper {
    position: relative;
    z-index: 1;
  }
</style>


Welcome to the Mouse vs AI: Robust Visual Foraging Competition @  **NeurIPS 2025 Competition Track**.

Mice robustly navigate in a range of conditions like fog, maybe more robustly than self-driving cars, which can struggle with out-of-distribution conditions. Build an AI agent that can outcompete a mouse!

<center>
<div class="full-width-element">
<video width="45%" height="auto" controls="controls" autoplay loop muted>
  <source src="/assets/images/tesla_fog_cut.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<video width="45%" height="auto" controls="controls" autoplay loop muted>
  <source src="/assets/images/example_video_mice_blur.mp4" type="video/mp4">
  Your browser does not support the video tag.
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
       alt="Overview of the Mouse-vs-AI competition…"
       class="clickable-image">

  <figcaption class="fig-caption">
    <strong>Figure&nbsp;1.</strong> Overview of the <em>Mouse&nbsp;vs&nbsp;AI – Robust Visual Foraging Challenge</em>.
    <strong>(Left)</strong> Build an AI agent that plays the same VR foraging task as the mice.
    <strong>(Center)</strong> <u>Track 1</u> scores behavioural robustness: average and minimum success rate across one seen (fog) and three unseen perturbations.
    <strong>(Right)</strong> <u>Track 2</u> scores neural alignment: how well a linear readout from the agent’s visual-encoder activations predicts mouse V1 + HVA activity.
  </figcaption>
</figure>
<br> 
  

Robust visual perception under real-world conditions remains a major bottleneck for AI agents: a modest shift in image statistics can collapse performance that was near-perfect during training.
Biological vision, by contrast, is remarkably resilient. Mice trained for only a few hours under a clear scene continue to solve the same visually guided foraging task when degradations are introduced, showing only a modest drop in success.

The **Mouse vs AI: Robust Visual Foraging Challenge** turns that gap into a quantitative benchmark. Participants train artificial agents in the Unity environment used for the mouse experiments, with access to two conditions (clean and fog).
In each 5-second trial the agent receives visual information about the environment through 86 × 155 pixels grayscale images and must reach a randomly placed, visually cued target. During mouse training the target started near the animal and the start distance was increased whenever performance exceeded 70 % success; the provided NormalTrain, FogTrain and RandomTrain builds of the Game implement the same curriculum for agents. A third build, RandomTest, always places the target at the maximum distance, mirroring the final evaluation pipeline with the two provided conditions. The trained agent—visual encoder plus policy—is the **single submission used for both tracks**.

<blockquote class="track" markdown="1">
<strong>Track 1 — Visual Robustness</strong><br>
 Each submitted agent is evaluated under the two provided conditions and **three held-out perturbations** never seen during training. Performance is summarised by <strong>Average Success Rate (ASR)</strong> and <strong>Minimum Success Rate (MSR)</strong> across all conditions.<br> 

<div class="math-center">
$$
  \displaystyle 
  \text{Score}_{\text{1}}
    = \frac{\text{ASR} + \text{MSR}}{2}
$$
</div>
</blockquote>

<blockquote class="track" markdown="1">
<strong>Track 2 — Neural Alignment</strong><br>
To test whether robust behaviour coincides with mouse-like visual representations, we replay the mouse’s video through each frozen visual encoder, extract hidden activations, and fit a linear regression that maps those activations to simultaneously recorded spiking activity from mouse V1 and higher visual areas.
Unlike previous alignment challenges—where networks are optimised directly for neural activity prediction—we quantify the emergent alignment of encoders trained solely for foraging. During evaluation we perform linear regression on each layer’s hidden activations and score them via the mean <strong>Pearson correlation (ρ)</strong> between predicted and recorded neural activity across all <strong>N neurons</strong> . To avoid an advantage for larger models, the hidden activations are first reduced to 50 dimensions using PCA. The layer with the highest ρ becomes the agent’s final Track 2 score.<br> 

  <div class="math-center">
$$ 
  \text{Score}_{\text{2}}= \frac{1}{N}\sum_{i=1}^{N}\rho_i
$$ 
</div>
</blockquote>

The overarching goals are therefore (i) to identify architectural and training principles that support **visual robustness**, and (ii) to test whether those principles also yield **mouse-like internal representations**. By grounding evaluation in both behaviour and cortical activity, the challenge unifies reinforcement learning, robust computer vision, and systems neuroscience within a single task.

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
4. **Submit your model** — Package your trained models and follow the **[Submission Guide](submission-guide)**.

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
