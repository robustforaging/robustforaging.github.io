Training Guide — Windows Beta

This document summarises exactly the procedure described in the accompanying How to Train.pdf. Follow the numbered sections below to install dependencies, launch training, add your own model, and locate results.

1 · Prerequisite

Requirement

Details

Operating system

Windows 10/11 64‑bit (native or running in a VM).

Command‑line access

All steps assume the standard Command Prompt (cmd.exe).

Disk space

Allow ≥ 10 GB for the environment, dependencies, and checkpoints.

2 · Install Miniconda†

† Skip this section if Anaconda or Miniconda is already installed.

Open cmd.exe.

Download the installer:

curl -o Miniconda3-latest-Windows-x86_64.exe \
  https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

Run a silent install:

start /wait "" Miniconda3-latest-Windows-x86_64.exe \
     /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S \
     /D=%USERPROFILE%\Miniconda3

Activate Conda:

%USERPROFILE%\Miniconda3\Scripts\activate

You should now be able to run conda --version without errors.

3 · Create and activate the training environment

Change into the folder that contains mouse.yml (bundled with the executable):

cd path\to\exeFile

Create and activate the environment:

conda env create -n mouse2 -f mouse.yml
conda activate mouse2

mouse2 is a suggested name; choose any identifier you prefer.

One‑time path fix — open train.py in a text editor and replace the placeholder path to encoders.py with the real location inside your Conda environment. A typical path is:

C:/<username>/Miniconda3/envs/mouse2/Lib/site-packages/mlagents/trainers/torch/encoders.py

Use a search utility such as Everything if the file is hard to locate.

4 · Run the training script

From the same directory, execute:

python start.py

You will see usage information similar to:

Usage: python start.py [train|test] [options]
Training options:
  --runs-per-network R    Number of runs per network (default: 5)
  --run-id ID            Run identifier (default: Normal)
  --networks N1,N2,N3    Comma-separated list of networks to train
                          (choices: fully_connected, nature_cnn, simple, resnet)

4.1 Example training command

python start.py train --runs-per-network 1 --run-id Normal \
                     --network neurips,simple,fully_connected

Troubleshooting:  If progress appears only after you press ENTER, rerun in unbuffered mode:

python -u start.py train --runs-per-network 1 --run-id Normal \
                        --network neurips,simple,fully_connected

If the issue persists, terminate the session and restart training.

5 · Customise the model

Add your custom model file to the Encoders/ directory.

If desired, modify hyper‑parameters in nature.yml but keep vis_encode_type: nature_cnn.

Re‑run the training command from § 4 to train with the new encoder.
