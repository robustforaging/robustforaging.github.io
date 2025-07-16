---
permalink: /training-guide-linux/
title: "Training Guide for Linux"
classes: wide
sidebar:
   nav: "guides"
---
Welcome to **Mouse vs. AI: Robust Visual Foraging Challenge @ NeurIPS 2025**

This is a training guide for **Linux** (Ubuntu and other distributions). For other operating systems, please check:
[Windows](/training-guide-win/) and [macOS](/training-guide-macos/)

# Install conda
Open command prompt
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

Press ```ENTER``` or type ```yes``` when prompted

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
💡 Troubleshooting: if the CUDA version isn’t compatible with your GPU, please try: 
```bash
pip install torch==1.8.1+cu111 -f https://download.pytorch.org/whl/torch_stable.html
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
```text
Usage: python train.py [options]

Training options:
  --runs-per-network R    Number of runs per network (default: 5)
  --env ID                Run identifier (default: Normal) [defines type of environment]
  --network N1,N2,N3     Comma-separated list of networks to train
                         (default choices: ['fully_connected', 
                         'nature_cnn', 'simple', 'resnet'])
                          You can specify your own custom networks here as 
                          well. Just list their names, separated by commas.
```

Example command for training:

```bash
python train.py --runs-per-network 1 --env RandomTrain --network MyNetwork1, MyNetwork2
```
- 💡 Troubleshooting: If training only proceeds after pressing ```ENTER```, try running the command with unbuffered output mode:  ```python -u train.py [options]``` 
- If the issue persists, stop the current training episode and train again

## Evaluating
```text
Usage: python evaluate.py [options]

Evaluation options:
  --model      Path to the trained ONNX model file
  --episodes   Number of episodes to run in inference(default: 50)
  --env        Build folder name under ./Builds/
  --log-name   Base name for the output log file
```

Example command for evaluation:
```bash
python evaluate.py --model "/path/to/your_model.onnx" --log-name "example.txt" --episodes 10
```

# Customize the model
- To add architecture: 
  - Add your model (e.g., `MyNetwork1.py`) to the `/mouse_vs_ai_linux/Encoders` directory
  - To train your custom network, run ```python train.py --network MyNetwork1 [options]```
- To adjust hyperparamters: 
  - Edit parameters in `/mouse_vs_ai_linux/Encoders/nature.yaml` file
  - 📝 Note: Please do not change the name of this file or the parameter `vis_encode_type` in this file. Only modify other configuration values as needed.

After making your changes, run the Python training script as described above.


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
