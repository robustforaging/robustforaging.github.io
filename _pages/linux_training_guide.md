---
permalink: /training-guide-linux/
title: "Training Guide for Linux"
classes: wide
sidebar:
   nav: "guides"
---
Welcome to **Mouse vs. AI: Robust Visual Foraging Challenge @ NeurIPS 2025**

This is a training guide for **Linux** (Ubuntu and other distributions). For other operating systems, please check:
[Windows](/training-guide-win/) and [MacOS](/training-guide-macos/)

# Create conda environment
Open Terminal and navigate to the directory where you want to download the project.

Clone the repository from GitHub:
```bash
git clone https://github.com/robustforaging/mouse_vs_ai_linux.git
cd mouse_vs_ai_linux
```

Then, create and activate the conda environment:
```bash
conda env create -n mouse2 --file mouse_linux.yml
conda activate mouse2
```

# Set executable permissions for Linux binaries
Make the Linux executable files executable:
```bash
# Make the binary executable
chmod +x ./Builds/RandomTrain/LinuxHeadless.x86_64

# If you have other build directories, make their executables executable too
# For example:
# chmod +x ./Builds/RandomTest/LinuxHeadless.x86_64
```

❗ Important:
Replace `./Builds/RandomTrain/LinuxHeadless.x86_64` with the actual path to your Linux executable file.
You need to run this command for each executable you intend to run.

# Install additional dependencies (if needed)
If you encounter any missing dependencies, you might need to install them:
```bash
# For Ubuntu/Debian systems
sudo apt update
sudo apt install -y libgl1-mesa-glx libglib2.0-0 libxext6 libsm6 libxrender1

# For systems with missing audio libraries
sudo apt install -y libasound2-dev
```

# Modify file path
Open `train.py` and go to line 134 (where `replace.replace_nature_visual_encoder` is called).
Update the path to point to the location of `encoders.py` in your conda environment.

💡 Tip: The `encoders.py` file is usually located in your conda environment's directory. For example: 
- Conda: `/home/<username>/miniconda3/envs/mouse2/lib/python3.8/site-packages/mlagents/trainers/torch`
- Anaconda: `/home/<username>/anaconda3/envs/mouse2/lib/python3.8/site-packages/mlagents/trainers/torch`

You can find the exact path using:
```bash
conda activate mouse2
python -c "import mlagents.trainers.torch; print(mlagents.trainers.torch.__file__.replace('__init__.py', 'encoders.py'))"
```

# Run script
## Training
```bash
python train.py --runs-per-network 1 --env RandomTrain --network neurips,simple,fully_connected,resnet,alexnet
```

## Evaluating
```bash
python evaluate.py --model "/home/<your_username>/path/to/your_model.onnx" --log-name "example.txt" --episodes 10
```

❗ Important:
Replace `/home/<your_username>/path/to/your_model.onnx` with the full path to your own ONNX model file on your machine.

# Troubleshooting
## Display issues
If you encounter display-related errors, you might need to set up your display environment:
```bash
export DISPLAY=:0
```

## GPU support
For GPU training (if available), ensure you have the appropriate CUDA drivers installed:
```bash
# Check if CUDA is available
nvidia-smi

# Install PyTorch with CUDA support if needed (after activating the conda environment)
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```
