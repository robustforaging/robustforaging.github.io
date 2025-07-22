---
layout: splash
permalink: /submission-guide/
title: "Submission Guide"
---

# Submission Guide

Welcome to the submission page for the **Mouse vs AI: Robust Visual Foraging Challenge** at NeurIPS 2025.

**Submit via Codabench:**  
[https://www.codabench.org/competitions/9453/](https://www.codabench.org/competitions/9453/)  
You may submit up to **5 models per team per day**.

---

## Final Evaluation Requirements

**Note:** Submitting a model is sufficient to appear on the leaderboard.  
However, to be considered for inclusion in the NeurIPS workshop and the post-competition summary paper, **top-performing teams must also provide a minimal training pipeline**. This can be submitted after the leaderboard deadline, but is required for final recognition and transparency.

---

## 1. Prepare Your Submission

- **Required**: Include your trained model in `.onnx` format.
- **Optional but required for workshop inclusion**: Submit a minimal training pipeline to allow retraining of your model (this can also be submitted retrospectively).
- **Optional**: Add a short model description (`.txt` or `.pdf`) outlining your architecture, training procedure, and any notable design choices. You may also submit this description later using this  
  [Google Form](https://docs.google.com/forms/d/e/1FAIpQLSdIvZk0fZhpO0u-bqwRpFUFcg61gMQ8Bqtq3tG3qbds2WfEWA/viewform).
- Combine all files into a single `.zip` archive before submitting.

---

## 2. Submit Your Model

1. Log in to your Codabench account.
2. Navigate to the "My Submissions" tab.
3. Click "Upload Submission", select your `.zip` file, and fill in the required fields.

---

## 3. Evaluation and Leaderboard

- Your model will be automatically evaluated on our standardized test environments.
- Results will be posted on the public leaderboard after evaluation completes.
- Final scores will be based on performance on a **private held-out test set** evaluated by the organizers.

---

## Competition Rules

- The competition is open to all researchers, students, and teams worldwide.
- Participants may use any training method, architecture, or data augmentation approach.
- Public datasets, pretrained models, and open-source libraries may be used for training.
- All submissions must run entirely offline, without internet access.
- No training is performed during evaluation—**inference only**.
- Submissions must be compatible with the interface provided in the [starter kit](https://github.com/robustforaging/starter-kit).
- Metadata (e.g., configuration files or logs) can be included for reproducibility, but are not required.
- Final evaluation and ranking will be performed on hidden test conditions.
- Top teams will be invited to contribute short reports for the NeurIPS workshop and summary publication.

--- 
For questions or technical issues, please reach out via [Discord](https://discord.gg/7mJPh5QMB7)


