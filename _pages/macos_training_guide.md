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

# Install conda 
Open the command prompt:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -p $HOME/miniconda
```
In order to initialize after the installation process is done, first run ```source <path to conda>/bin/activate``` and then run ```conda init --all```.

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
You may also need to install pandas separately: ```pip install pandas```

#  Give permission to a MacOS app
```bash
# Make the app's binary executable
chmod +x ./Builds/RandomTrain/RandomTrain.app/Contents/MacOS/*

# Remove the 'quarantine' flag applied by macOS (for downloaded apps)
xattr -dr com.apple.quarantine ./Builds/RandomTrain/RandomTrain.app
```
❗ Important:
Replace ```./Builds/RandomTrain/RandomTrain.app``` with the actual path to your .app bundle in both commands.
You need to run these commands for each app you intend to execute if macOS flags it.


# Modify file path
Open ```train.py``` and go to line 137 (where ```replace.replace_nature_visual_encoder``` is called).
Update the path to point to the location of ```encoders.py``` in your conda environment.

📝 Note: The ```encoders.py``` file is usually located in your conda environment’s working directory. For example: ```/miniconda3/envs/mouse/lib/python3.8/site-packages/mlagents/trainers/torch```



# Run script
## Training
```text
Usage: python train.py [options]

Training options:
  --runs-per-network R    Number of runs per network (default: 5)
  --env ID                Run identifier (default: Normal) [defines 
                          type of environment]
  --network N1,N2,N3      Comma-separated list of networks to train
                          (default choices: ['fully_connected', 
                          'nature_cnn', 'simple', 'resnet'])
                          You can specify your own custom networks here as 
                          well. Just list their names, separated by commas.
```

Example command for training:
```bash
python train.py --runs-per-network 1 --env RandomTrain --network MyNetwork1
```
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
❗ Important:
Replace ```/path/to/your_model.onnx``` with the full path to your own ONNX model file on your machine.

# Customize the model
- To add architecture: 
  - Add your model (e.g., `MyNetwork1.py`) to the `/mouse_vs_ai_macOS/Encoders` directory
  - To train your custom network, run ```python train.py --network MyNetwork1 [options]```
- To adjust hyperparamters: 
  - Edit parameters in `/mouse_vs_ai_macOS/Encoders/nature.yaml` file
  - 📝 Note: Please do not change the name of this file or the parameter `vis_encode_type` in this file. Only modify other configuration values as needed.

After making your changes, run the Python training script as described above.
