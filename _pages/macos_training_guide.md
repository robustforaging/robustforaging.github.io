---
permalink: /training-guide-macos/
title: "Training Guide for MacOS"
classes: wide
sidebar:
   nav: "guides"
---
Welcome to **Mouse vs. AI: Robust Visual Foraging Challenge @ NeurIPS 2025**

This is a training guide for **macOS**. For other operating systems, please check:
[Windows](/training-guide-win/) and [Linux](/training-guide-linux/)

# Create conda environment
Open Terminal and navigate to the directory where you want to download the project.

Clone the repository from GitHub:
```bash
git clone https://github.com/robustforaging/mouse_vs_ai_macOS.git
cd mouse_vs_ai_macOS
```

Then, create and activate the conda environment:
```bash
CONDA_SUBDIR=osx-64 conda env create -n mouse --file mouse.yml
conda activate mouse
```

#  Give Permission to a macOS App
```bash
# Make the app's binary executable
chmod +x ./Builds/RandomTrain/RandomTrain.app/Contents/MacOS/*

# Remove the 'quarantine' flag applied by macOS (for downloaded apps)
xattr -dr com.apple.quarantine ./Builds/RandomTrain/RandomTrain.app
```
❗ Important:
Replace ./Builds/RandomTrain/RandomTrain.app with the actual path to your .app bundle in both commands.
You need to run these commands for each app you intend to execute if macOS flags it.


# Modify file path
Open ```train.py``` and go to line 137 (where ```replace.replace_nature_visual_encoder``` is called).
Update the path to point to the location of ```encoders.py``` in your conda environment.

💡 Tip: The ```encoders.py``` file is usually located in your conda environment’s working directory. For example: ```/miniconda3/envs/mouse/lib/python3.8/site-packages/mlagents/trainers/torch```



# Run script
## Training
```bash
python train.py --runs-per-network 1 --env RandomTrain --network neurips,simple,fully_connected,resnet,alexnet
```
## Evaluating
```bash
python evaluate.py --model "/Users/<your_username>/path/to/your_model.onnx" --log-name "example.txt" --episodes 10
```
❗ Important:
Replace ```/Users/<your_username>/path/to/your_model.onnx``` with the full path to your own ONNX model file on your machine.
