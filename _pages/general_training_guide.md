---
permalink: /general_training_guide/
title: "Training Guide"
classes: wide
sidebar:
   nav: "guides"
---

Welcome to **Mouse vs. AI: Robust Visual Foraging Challenge @ NeurIPS 2025**

This is a general training guide for the Mouse vs. AI NeurIPS 2025 competition.

For platform specific instructions on how to download the environment and train an agent please check:
[Windows](/training-guide-windowsI/), [Linux](/training-guide-linux/) and [macOS](/training-guide-macos/)


## General instructions
The task for virtual and biological agents is to reach a randomly placed target within a time window of 5 seconds. In the beginning of the training of mice the rtarget was placed close to them and target distance was increases incrementally when agents hit a 70% succesor rate.
Mice were trained on the normal condition before there performance under unseen visual perturbations was tested. 



<figure class="competition-diagram">
  <img src="/assets/images/Figure_unity.png"
       alt="Overview of the Mouse-vs-AI competition…">

  <figcaption class="fig-caption">
    <strong>Figure&nbsp;1.</strong> Overview of the <em>Mouse&nbsp;vs&nbsp;AI – Robust Visual Foraging Challenge</em>.
    <strong>(Left)</strong> Build an AI agent that plays the same VR foraging task as the mice.
    <strong>(Center)</strong> <u>Track 1</u> scores behavioural robustness: average and minimum success rate across one seen (fog) and three unseen perturbations.
    <strong>(Right)</strong> <u>Track 2</u> scores neural alignment: how well a linear readout from the agent’s visual-encoder activations predicts mouse V1 + HVA activity.
  </figcaption>
</figure>

## The environment builds
- we provide 4 different builds, 3 are mainly inteneded for training and 1 for testing but you can use them in any way you wish.
The three training environments (NormalTrain,FogTrain and RandomTrain) start witht he target being placed close to the agents starting point and and soon as your agent reeaches a succesor rate of 70% the target distances is increased up to the maximum distance of 5.
All environment builds have the same task and just differ in the visual scene. NormalTrain only has the unterpertubed visual scene while FogTrain only consist of fog trailsand RandomTrain alternates between normal and fog trails

Morever The RandomTest build is intended for you to get an idea of how well your agent performs. The RandomTest biold starts with the target being randomly placed at maximum distance and alternates trials between the two provided conditions (normal and fog).

## Training with ML agents
- describe the config file
- what parameters mean or refer to ml agents document page




## Evaluation
Once you submit a model we will evaluate it by testing your agents performance on trials where the target is placed at the maximum distance on all provided + 3 additional held out perturbations.

Track 1 will score your agents performance based on two metrics: the average success rate across  all conditions (ASR) and the minimum success rate (MSR) across all conditions, to capture the worst case generlization. The final score for track 1 will be calcuclated as follows Score_{Track 1} = 0.5*ASR+0.5*MSR

Track 2 will be evaluated based on the ability of a linear regression model to predict neural responses from the agents visual encoders hidden activations. We will provide a track two evaliuation script and a few minutes of data to allow you to asses your agents alignment with mouse visual cortex acitivty.
The final evaluation is conductated on a held-out test set of stimulus-response pairs and quantified as the mean pearson correlation between predicted and recorded neural activity, averaged across all recorded neurons.
 Add link yo sumbisison guide:
##
