---
permalink: /training-guide-win/
title: "Training Guide for Windows"
classes: wide
sidebar:
   nav: "guides"
---

Welcome to **Mouse vs. AI: Robust Visual Foraging Challenge @ NeurIPS 2025**

This is a training guide for **Windows**. For other operating systems, please check:
[Linux](/training-guide-linux/) and [macOS](/training-guide-macos/)

# Install conda
Open command prompt
```bash
curl -o Miniconda3-latest-Windows-x86_64.exe
start /wait "" Miniconda3-latest-Windows-x86_64.exe /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S /D=%USERPROFILE%\Miniconda3
```
To activate conda, do: ```%USERPROFILE%\Miniconda3\Scripts\activate```

# Create conda environment
Open command prompt and navigate to the directory where you want to download the project.

Clone the repository from GitHub:
```bash
git clone https://github.com/robustforaging/mouse_vs_ai_windows.git
cd mouse_vs_ai_windows
```

Then, create and activate the conda environment:
```bash
conda env create -n mouse -f mouse.yml
conda activate mouse
``` 

You may need to install pandas separately: ```pip install pandas```

# Modify file path
Open ```train.py``` and go to line 134 (where ```replace.replace_nature_visual_encoder``` is called).
Update the path to point to the location of ```encoders.py``` in your conda environment.

💡 Tip: The ```encoders.py``` file is usually located in your conda environment’s working directory. For example: ```C:/…/miniconda3/env/mouse2/Lib/site-packages/mlagents/trainers/torch/encoders.py```


# Run script

## Training
```text
Usage: python train.py [options]

Training options:
  --runs-per-network R    Number of runs per network (default: 5)
  --env ID                Run identifier (default: NormalTrain) [defines type of environment]
  --network N1,N2,N3      Comma-separated list of networks to train
                          (default choices: ['fully_connected', 
                          'nature_cnn', 'simple', 'resnet'])
                          You can specify your own custom networks here as 
                          well. Just list their names, separated by commas.
```

Example command for training:
```bash
python train.py --runs-per-network 1 --env NormalTrain --network MyNetwork1
```
- Troubleshooting: If training only proceeds after pressing ```ENTER```, try running the command with unbuffered output mode:  ```python -u train.py [options]``` 
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
❗ Important: Replace `/path/to/your_model.onnx` with the full path to your own ONNX model file on your machine.

# Customize the model
- To add architecture: 
  - Add your model (e.g., `MyNetwork1.py`) to the `/mouse_vs_ai_windows/Encoders` directory
  - To train your custom network, run ```python train.py --network MyNetwork1 [options]```
- To adjust hyperparamters: 
  - Edit parameters in `/mouse_vs_ai_windows/Encoders/nature.yaml` file
  - 📝 Note: Please do not change the name of this file or the parameter `vis_encode_type` in this file. Only modify other configuration values as needed.

After making your changes, run the Python training script as described above.

