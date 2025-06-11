---

layout: page
title: "Training Guide"
description: "Step‑by‑step instructions for training your first agent with the Windows v0.9 build. (A Linux headless workflow will ship in v1.0.)"
nav\_order: 2
-------------

<!--
This markdown is **copy‑paste ready** for a Jekyll site using the *minima* theme (or any theme that respects kramdown).
-->

# Training Guide v0.9

> **Beta notice** — This guide targets the *Windows* `.exe` release only.
> A Docker‑based Linux workflow and new headless binary will land in **v1.0 (July 2025)**.

---

## 0 · Download the environment

| File                                                                                               | Size    | SHA‑256                  |
| -------------------------------------------------------------------------------------------------- | ------- | ------------------------ |
| [`MouseVsAI_Windows_v0.9.zip`](https://robustforaging.github.io/assets/MouseVsAI_Windows_v0.9.zip) |  ≈ 3 GB | `TODO‑REPLACE‑WITH‑HASH` |

Un‑zip somewhere short, e.g. `C:\MouseVsAI\`. You should now have:

```
C:\MouseVsAI\
├── MouseVsAI.exe
└── MouseVsAI_Data\  (resources)
```

---

## 1 · Prerequisites

| Requirement        | Notes                                                                                |
| ------------------ | ------------------------------------------------------------------------------------ |
| **OS**             | Windows 10/11 64‑bit or a Windows VM.                                                |
| **Disk space**     |  ≥ 10 GB free (environment + logs + checkpoints).                                    |
| **GPU (optional)** | Any recent NVIDIA card (`> GTX 1060`) speeds training ×5. CPU‑only is OK but slower. |
| **Python**         | We recommend **Miniconda 3** + the environment file below.                           |

### 1.1 Install Miniconda (skip if already installed)

```powershell
curl -o Miniconda3-latest-Windows-x86_64.exe `
  https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

start /wait "" Miniconda3-latest-Windows-x86_64.exe `
  /InstallationType=JustMe /AddToPath=1 /RegisterPython=1 /S `
  /D=%USERPROFILE%\Miniconda3
```

Open a new **Command Prompt** and run `conda --version` to confirm installation.

---

## 2 · Create the Conda environment

```powershell
cd C:\MouseVsAI
conda env create -n mouse2 -f mouse.yml   # installs PyTorch, ML‑Agents, etc.
conda activate mouse2
```

---

## 3 · Launch the Unity environment (optional test)

```powershell
MouseVsAI.exe -batchmode -nographics --mlagents-port 5005
```

The window stays black because rendering is disabled (`-nographics`) — that’s expected.
Press **Ctrl+C** to exit.

---

## 4 · Start training

All helper scripts live in `starter_kit/`. The main entry point is **`start.py`**.

```powershell
python start.py train --run-id vanilla --network neurips \
                     --runs-per-network 1
```

**Common flags**

| Flag                 | Meaning                                                                                |
| -------------------- | -------------------------------------------------------------------------------------- |
| `--network`          | Comma‑separated list of encoder names (`fully_connected`, `nature_cnn`, `neurips`, …). |
| `--runs-per-network` | How many independent seeds per encoder (default = 5).                                  |
| `--time-scale`       | Unity speed‑up factor (higher = faster, default = 20).                                 |
| `--mlagents-port`    | Change if port 5005 is busy (must match exe).                                          |

`checkpoints/` and TensorBoard logs are written to `results/vanilla/`.

---

## 5 · Evaluate a checkpoint

```powershell
python start.py test --checkpoint results/vanilla/neurips/best.onnx \
                     --mlagents-port 5005
```

Success rate is printed in the console. The agent should reach the target in < 5 s under the clean condition.

---

## 6 · Package your submission

1. Pick the **best `.onnx`** file from `results/`.
2. Copy it to `submission/agent.onnx`.
3. Include **`metadata.json`** describing encoder, seeds, and compute budget.
4. Zip the `submission/` folder and upload via the leaderboard portal.

> **Track 2 note** — For Neural Alignment, also include your trained **`readout.npz`** file.

---

## 7 · Troubleshooting

| Symptom                                  | Likely cause                         | Quick fix                                             |
| ---------------------------------------- | ------------------------------------ | ----------------------------------------------------- |
| `Unable to connect to Unity environment` | Port 5005 busy or mismatched         | Pass `--mlagents-port 6000` to *both* exe and script. |
| Training stalls after first line         | Std‑out buffering in PowerShell      | Add `-u` (`python -u start.py ...`).                  |
| FPS < 20 even on GPU                     | `--time-scale` too high for hardware | Lower to `10` or use smaller `--runs-per-network`.    |

Need help? Join **#training-help** on Discord or open a GitHub issue.

---

## 8 · What’s next?

* **v1.0** (ETA July 2025) — headless Linux build + Docker image for cluster training.
* **Starter notebooks** for Track 2 alignment.
* **Leaderboard refresh** every Monday (PST).

Happy training — and may your agent be as robust as a mouse! 🎯
