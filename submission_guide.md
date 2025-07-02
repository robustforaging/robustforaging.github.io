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
Model Submission Guide
Use the GitHub-based submission workflow below to upload your ONNX model(s). Once your pull request is merged into main, our automated evaluation script will run and update the public leaderboard.

## 1. Fork & Clone the Submission Repository

1. Fork the official repo to your account:
https://github.com/robustforaging/mouse_vs_ai_submissions → Fork

2. Clone your fork locally (choose HTTPS or SSH):

```
bash
# HTTPS (you’ll need a GitHub Personal Access Token in place of your password)
git clone https://github.com/<YOUR_GITHUB_USERNAME>/mouse_vs_ai_submissions.git  

# — or —  

# SSH (if you have SSH keys set up)
git clone git@github.com:<YOUR_GITHUB_USERNAME>/mouse_vs_ai_submissions.git

cd mouse_vs_ai_submissions
```

## 2. Create a Submission Branch
Create one feature branch for your submission. If you wish to submit multiple models in one PR, pick a descriptive branch name (e.g. submit-MyTeam-multiple-models).

```
bash
git checkout -b submit-<TeamName>-<ModelName>
```

<TeamName>: your team or handle (no spaces)
<ModelName>: a short, unique name for this model

## 3. Add Your ONNX Model(s)
Inside your repo, under submissions/, create a directory for your team:

```
submissions/<TeamName>/
```

Copy your ONNX file(s) there.

For a single model:

```
submissions/MyTeam/MyModel.onnx
```

For multiple models in one PR, simply place each under the same folder:
```
submissions/MyTeam/ModelA.onnx
submissions/MyTeam/ModelB.onnx
```

Tip: If you’re adding files to a brand-new folder, Git may ignore it. You can add an empty placeholder (.gitkeep) alongside your .onnx files, but as soon as you add your real model files, the folder will no longer be empty and will be tracked.

## 4. Commit & Push

```
git add submissions/<TeamName>/*.onnx
git commit -m "Submit model(s) for <TeamName>: <ModelName>[, <ModelName2>…]"
git push -u origin submit-<TeamName>-<ModelName>
```

## 5. Open a Pull Request
In your GitHub fork, you’ll see a banner: Compare & pull request.

Click it, target the upstream repo’s main branch, and fill out the PR form using our template:

```
## Submission metadata

- **Team Name**: MyTeam  
- **Affiliation**: MyLab / MyCompany  
- **Model file(s)**: 
  - `submissions/MyTeam/MyModel.onnx`
  - (optional) `submissions/MyTeam/ModelB.onnx`
- **How we ran it** (optional): 
Submit the PR. You can update this same PR if you need to add or revise model files—just commit & push to the same branch.
```

## 6. After Your PR Is Merged
Your model file(s) become public under submissions/MyTeam/.

Our CI automatically runs evaluate.py on each file and updates the public leaderboard.

You’ll see your score published in leaderboard.md.

FAQs
Can I submit multiple models in one PR?
Yes—just place each .onnx under submissions/<TeamName>/ and list them in your PR description.

What if I need to update my model?
Push additional commits to the same submit-… branch before your PR is merged.

Will my model be public?
Yes—submissions are by default visible. If you require confidentiality, please contact the organizers.

Good luck, and happy foraging! 🎉



---

Need help? Ping **@organisers** in the Discord or open an issue in the GitHub starter kit.
-->
