---
layout: page
title: "Training Guide"
description: "Professional walkthrough for training an agent with the current Windows executable. A Linux headless workflow will be published separately."
nav_order: 2
---
> The current training guide targets the **v0.9 Windows executable** that ships with built-in ML-Agents.  
> A forthcoming v1.0 (July,1 2025) will provide a stand-alone Python API (no ML-Agents) + headless Linux builds for cluster training



Follow the numbered sections below to install dependencies, launch training, add your own model, and locate results.

## 1 · Download Environment

Download environment [MouseVsAI_Windows_v0.9.zip](https://drive.google.com/file/d/1S7KtiVVI5LaxVFGQlHjV0A1DzFGyklYo)

## 2 · Install Miniconda <sup>†</sup>

<sup>† Skip this section if you already have Anaconda or Miniconda.</sup>

   a) Download the installer:
   {% highlight cmd %}
      curl -o Miniconda3-latest-Windows-x86_64.exe ^
           https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe
   {% endhighlight %}
   
   b) Silent install
   {% highlight cmd %}
      start /wait "" Miniconda3-latest-Windows-x86_64.exe ^
     /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S ^
     /D=%USERPROFILE%\Miniconda3
   {% endhighlight %}
   
   c) Activate
   {% highlight cmd %}
   %USERPROFILE%\Miniconda3\Scripts\activate
   {% endhighlight %}

Check installation:
   {% highlight cmd %}
   conda --version
   {% endhighlight %}

   
## 3· Create and activate the training environment
   {% highlight cmd %}
   cd <folder‑with‑exe-and-mouse.yml>
   conda env create -n mouse2 -f mouse.yml
   conda activate mouse2
   {% endhighlight %}
   
   One‑time path fix
   Open train.py and replace the placeholder path to encoders.py with the actual path inside your environment, e.g.
   C:/<user>/Miniconda3/envs/mouse2/Lib/site-packages/mlagents/trainers/torch/encoders.py

## 4· Run the training script
   {% highlight cmd %}
   python start.py
   {% endhighlight %}

The script prints usage:
   {% highlight cmd %}
   Usage: python start.py [train|test] [options]
     --runs-per-network R
     --run-id ID
     --networks N1,N2,N3   (fully_connected, nature_cnn, simple, resnet)
   {% endhighlight %}

The script prints usage:
   {% highlight cmd %}
   python -u start.py train ^
          --runs-per-network 1 ^
          --run-id Normal ^
          --network neurips,simple,fully_connected
   {% endhighlight %}

## 5· Customise the model
   Add your custom encoder to the Encoders/ directory.
   Optionally tweak hyper‑parameters in nature.yml (keep vis_encode_type: nature_cnn).
   Re‑run the command from § 4.


