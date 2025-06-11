---
layout: page
title: "Training Guide (Windows .exe)"
description: "Professional walkthrough for training an agent with the current Windows executable. A Linux headless workflow will be published separately."
nav_order: 2
---

# Training Guide — Windows Beta

This document summarises **exactly** the procedure described in the accompanying *How to Train.pdf*. Follow the numbered sections below to install dependencies, launch training, add your own model, and locate results.

---

## 1 · Prerequisite

| Requirement      | Details                                          |
|------------------|--------------------------------------------------|
| Operating system | **Windows 10/11 64-bit** (native or in a VM).    |
| Command-line     | All steps assume the standard **Command Prompt** |
| Disk space       | **≥ 10 GB** for the env, dependencies, checkpoints |

---

## 2 · Install Miniconda <sup>†</sup>

<sup>† Skip this section if you already have Anaconda or Miniconda.</sup>

1. Open **cmd.exe**.  
2. Download the installer:

   ```cmd
   curl -o Miniconda3-latest-Windows-x86_64.exe ^
        https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe
   
3.Run a silent install:

   ```cmd
  start /wait "" Miniconda3-latest-Windows-x86_64.exe ^
       /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S ^
       /D=%USERPROFILE%\Miniconda3

4. Activate Conda:

    %USERPROFILE%\Miniconda3\Scripts\activate

Verify with conda --version.

## 3 · Create & activate the training environment

cd path\to\exeFolder          :: folder that contains mouse.yml
conda env create -n mouse2 -f mouse.yml
conda activate mouse2

    mouse2 is just a suggestion—use any env name you like.

One-time path fix
Open train.py and replace the placeholder path to encoders.py with the actual path inside your conda env, e.g.:

C:/<username>/Miniconda3/envs/mouse2/Lib/site-packages/mlagents/trainers/torch/encoders.py


