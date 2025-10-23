# MERCI
Multimodal Dataset for Personalised and Emotionally-Aware Dialogues
# MERCI: A Multimodal Dataset for Personalised and Emotionally-Aware Dialogues

[![Conference](https://img.shields.io/badge/CBMI-2025-blue)](#)
[![License: Code](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![License: Dataset](https://img.shields.io/badge/Dataset-CC%20BY--NC%204.0-orange)](DATASET_LICENSE)
[![Status](https://img.shields.io/badge/Data-Access%20upon%20publication-informational)](#data-access)

**MERCI** is a compact, high-depth **multimodal** corpus of *real human–robot dialogues* with **tri-view video**, **audio**, **ASR text**, and **user profiles**, designed to enable **personalised** and **emotion-aware** conversational AI.

> Paper: “MERCI: A Multimodal Dataset for Personalised and Emotionally-Aware Dialogues”, **CBMI 2025**.  
> Contact / corresponding author: mohammed.s.althubyani@uts.edu.au

---

## Overview

- **Modalities:** tri-view video (head / front / side), audio, transcripts (Whisper ASR), user profiles  
- **Labels (assistive cues):** sentiment (lexicon-based), facial expressions (MobileNetV2), SSD + NMS for detection  
- **Scale:** ~30 participants, ~1,860 utterances, synchronised and time-aligned  
- **Ethics:** UNSW iRECS4630; data release via DUA (see below)

### Tri-view capture

<p align="center">
  <img src="assets/tri_head.jpg" width="31%" alt="Head camera (robot view)">
  <img src="assets/tri_external_front.jpg" width="31%" alt="External front camera">
  <img src="assets/tri_side.jpg" width="31%" alt="External side camera">
</p>

<p align="center"><em>Tri-view video streams aligned with audio and ASR text.</em></p>

---
### Interaction overview

<p align="center">
  <img src="assets/overview.png" width="80%" alt="Overview of MERCI interaction flow (user–robot–ASR–sentiment–FER)">
</p>


### Annotation & pipeline checks (assistive labels)

<p align="center">
  <img src="assets/pipeline.png" width="95%" alt="Pipeline: Whisper ASR, sentiment analysis, MobileNetV2 FER, SSD+NMS, alignment">
</p>

- Whisper ASR with **word/sentence error rate** (WER/SER)
- Sentiment analysis (lexicon-based)
- Facial expression cues (MobileNetV2) with SSD + **non-maximum suppression**
- Time alignment & quality checks
- Labels are **assistive**, not ground truth of internal state
---

## Repository structure

MERCI/
├─ assets/ # figures (tri-view, pipeline, charts, QR)
├─ baselines/ # (to be added) training/eval scripts
├─ results/ # (to be added) CSVs from the paper
├─ DATA_ACCESS.md # how to request the dataset (DUA)
├─ DATASET_LICENSE # CC BY-NC 4.0
├─ LICENSE # code license (MIT or Apache-2.0)
├─ CITATION.cff # citation metadata
└─ README.md


---

## Baselines & tasks

We provide code (after publication) and results for:
- **Emotion classification** (reporting accuracy, precision, recall, F1; macro-averaged where relevant)  
- **Sentiment regression** (MAE, RMSE, CCC)  
- **Emotion-aware response generation** (BLEU-1/2, ROUGE-L, METEOR, perplexity)

### Key results (from the paper)

> Replace `TBD` with exact numbers later. You may also export your result tables as images into `assets/` and embed them.

**Classification (macro-F1 ↑)**

| Model            | Macro-F1 | F1 (Neutral) | F1 (Positive) | F1 (Negative) |
|------------------|---------:|-------------:|--------------:|--------------:|
| Transformer-A    |   TBD    |      TBD     |      TBD      |      TBD      |
| Transformer-B    |   TBD    |      TBD     |      TBD      |      TBD      |

**Sentiment regression**

| Model         | MAE ↓ | RMSE ↓ | CCC ↑ |
|---------------|------:|-------:|------:|
| Baseline-X    |  TBD  |  TBD   |  TBD  |
| Baseline-Y    |  TBD  |  TBD   |  TBD  |

**Emotion-aware generation**

| Model / Prompting         | BLEU-1 ↑ | BLEU-2 ↑ | ROUGE-L ↑ | METEOR ↑ | PPL ↓ |
|---------------------------|---------:|---------:|----------:|---------:|------:|
| GPT-4 (emotion-aware)     |   TBD    |   TBD    |   TBD     |   TBD    |  TBD  |
| GPT-3.5 (vanilla)         |   TBD    |   TBD    |   TBD     |   TBD    |  TBD  |

> Notes: labels from facial expressions and sentiment analysis are **assistive** signals, not ground truth of internal affect.

---

## Data access

The dataset will be released **upon publication** for **non-commercial academic use**.

- **Licence:** CC BY-NC 4.0 (dataset)  
- **Access:** via a **Data Use Agreement (DUA)** aligned with UNSW ethics (**iRECS4630**)  
- **How to request:** see [`DATA_ACCESS.md`](DATA_ACCESS.md) (form/email link will be added here)

Code for baselines will be added to this repository after publication.

---

## Getting started (code – coming soon)

```bash
# after we push code:
git clone https://github.com/<your-org-or-user>/MERCI.git
cd MERCI
pip install -r requirements.txt

# classification
python baselines/train_cls.py --config configs/cls_transformer.yaml

# regression
python baselines/train_reg.py --config configs/reg_transformer.yaml

# generation (prompted)
python baselines/run_gpt_eval.py --task generation --split test

Ethics
MERCI was collected under UNSW ethics approval (iRECS4630). Video/audio contains identifiable data; redistribution is restricted. All releases require a signed DUA and compliance with the licence.

Citation
If you use MERCI or the baselines, please cite:
@inproceedings{Althubyani2025MERCI,
  title     = {MERCI: A Multimodal Dataset for Personalised and Emotionally-Aware Dialogues},
  author    = {Althubyani, Mohammed S. and Meng, Zhijin and Xie, Shengyuan and Cruz, Francisco and Razzak, Imran and Prasad, Mukesh and Sandoval, Eduardo B. and Kocaballi, Baki},
  booktitle = {Proc. {CBMI} 2025},
  year      = {2025},
  doi       = {TBD},
  note      = {Dataset access upon publication; CC BY-NC 4.0}
}

