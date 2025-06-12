---
layout: default
title: Submission
---

# Submission Guide

Each submission must include:
- A trained model file (.pt, .ckpt, or .onnx)
- Optional README or config for reproducibility

Submissions are evaluated centrally by the organizers on a held-out test set with visual perturbations.

---

# Submission Guide — v0.9 Beta

> **Scope** — These instructions apply to the Windows `.exe` beta. For the upcoming v1.0 Linux release the packaging format will stay identical, but the runner script will change.

---

## 1 · Submission checklist

|   | Item                 | Notes                                                                       |
| - | -------------------- | --------------------------------------------------------------------------- |
|   | Trained model files  | `.pt` or `.onnx`; see §2 for naming convention                              |
|   | `config.yaml`        | Snapshot of your training hyper‑parameters                                  |
|   | `metadata.txt`       | Team name, contact e‑mail, short description                                |
|   | Zip archive ≤ 500 MB | 7‑zip or standard `zip`; no `.rar`                                          |

---

## 2 · Folder structure & naming

Your archive **must** unpack into a single top‑level folder named after your run‑id:

```
MyAgent_Normal/                 <‑ top‑level folder
├── model_head.pt               <‑ weights file (PyTorch example)
├── config.yaml
└── metadata.txt
```

* **Multiple networks?** Package each network in its own folder and zip them
  together:

```
MyTeam_Submission_v2.zip
├── VisNet_Normal/
│   └── ...
└── ResNet_Perturb/
    └── ...
```


<!--
---

## 3 · Create the archive

```cmd
:: Windows PowerShell example
Compress-Archive -Path VisNet_Normal,ResNet_Perturb -DestinationPath MyTeam_Submission_v2.zip
```

Verify size ≤ 500 MB and compute a SHA‑256 checksum (recommended):

```cmd
CertUtil -hashfile MyTeam_Submission_v2.zip SHA256
```

---

## 4 · Local validation (strongly recommended)

Run the provided `validate_submission.py` script before uploading:

```cmd
conda activate mouse2
python tools\validate_submission.py --zip MyTeam_Submission_v2.zip \
       --env MouseVsAI_Windows_v0.9.exe --episodes 10
```

The script will:

1. Unpack the zip into a temp folder.
2. Load each model into the evaluation runner.
3. Play 10 short episodes to verify file integrity and runtime (< 10 s each).

If all checks pass, you’ll see `VALIDATION OK`.

---

## 5 · Upload to the leaderboard

1. Log in to the [https://mouse-vs-ai.](https://mouse-vs-ai.leaderboard.io)[*leaderboard*](https://mouse-vs-ai.leaderboard.io)[.io](https://mouse-vs-ai.leaderboard.io) portal.
2. Click **Submit** → **Upload Zip**.
3. Attach `MyTeam_Submission_v2.zip` and paste the SHA‑256 hash.
4. Agree to the rules and click **Submit**.
5. Refresh your team page; status will show **Queued → Running → Scored**.

> **Submission limit** — You may upload up to **3** zip files per week.
> Only the highest‑ranked model before the final deadline counts for prizes.

---

## 6 · Evaluation protocol

| Stage                       | Episodes | Perturbations               | Metrics   |
| --------------------------- | -------- | --------------------------- | --------- |
| Public leaderboard          | 50       | Same fog levels as training | ASR & MSR |
| Private leaderboard         | 100      | Held‑out perturbations      | ASR & MSR |
| (Optional) Neural alignment | 80       | No perturbation             | Pearson r |

Detailed scoring scripts live in the *starter‑kit/evaluation* folder.

---

## 7 · Common errors & fixes

| Error message                 | Likely cause                                 | Fix                                                               |
| ----------------------------- | -------------------------------------------- | ----------------------------------------------------------------- |
| `Model file not found`        | Wrong path inside archive                    | Keep `model_head.pt` at first level of each run folder            |
| `RuntimeError: size mismatch` | Wrong network architecture vs. saved weights | Ensure you export with the same class definition used in training |
| `Timeout after 5 min`         | Model too large or slow                      | Optimise inference (e.g., TorchScript) or contact organisers      |

---

## 8 · Licence & rules recap

* By submitting you grant the organisers a non‑exclusive licence to evaluate your model weights **only** for leaderboard purposes.
* Your code and data remain your intellectual property.
* Full rules: [rules.md](rules.html).

---

Need help? Ping **@organisers** in the Discord or open an issue in the GitHub starter kit.



