# Prompt Injection Detection Using Fine-Tuned Transformer Models with a Glass-Box Approach with Explainable AI

A dissertation project that detects prompt injection attacks by classifying prompts
as **SAFE** or **INJECTION** using fine-tuned BERT-variant transformer models, with
token-level explanations powered by SHAP and a deployable web application.

---

## Aim

To develop a machine-learning-based prompt injection detection system that is both
**accurate** and **interpretable**. The system fine-tunes lightweight BERT-variant
models (DistilBERT, RoBERTa, SecBERT) on public datasets, applies SHAP to explain
every prediction (the "glass-box" approach), and provides a practical web tool that
screens prompts before they reach a target Large Language Model (LLM).

## Objectives

- Collect and pre-process public prompt injection datasets.
- Fine-tune and compare three BERT-variant models (DistilBERT, RoBERTa, SecBERT) to
  find the best architecture for prompt injection detection.
- Integrate SHAP with the selected model to generate token-level attribution scores.
- Build a Flask/Streamlit web app returning a SAFE/INJECTION verdict, a confidence
  score, and a colour-highlighted token view.
- Evaluate the classifier with Accuracy, Precision, Recall, F1-score and AUC-ROC, and
  assess explanation quality with sufficiency and comprehensiveness metrics.

## Datasets

- **deepset/prompt-injections** — Hugging Face (deepset, 2023)
- **PromptShield** — Mendeley Data (Rahman et al., 2025)

## Models

- **DistilBERT** — lightweight baseline
- **RoBERTa** — robustly optimised BERT variant
- **SecBERT** — cybersecurity-domain BERT (or a verified alternative)

## Project structure

```
Prompt-Injection-Detection-System/
├── data/
│   ├── raw/         # original downloaded datasets
│   └── processed/   # cleaned, merged, split datasets
├── notebooks/       # Colab notebooks (data prep, training, SHAP)
├── models/          # saved fine-tuned models & tokenizers
├── src/             # Python scripts
├── webapp/          # Flask/Streamlit web application
├── results/         # metrics, charts, confusion matrices
├── screenshots/     # evidence images for the dissertation
└── docs/            # proposal, instructions, dissertation drafts
```

## Tech stack

Python, PyTorch, Hugging Face Transformers, scikit-learn, SHAP, Flask/Streamlit,
Google Colab (NVIDIA T4 GPU), Git/GitHub.

## Status

🚧 In development. Current progress:

- [x] Environment set up and verified (Google Colab, T4 GPU)
- [x] Project folder structure created
- [ ] Git/GitHub tracking
- [ ] Dataset preparation
- [ ] Model fine-tuning & evaluation
- [ ] SHAP explainability
- [ ] Web application
- [ ] Dissertation write-up

## Author

Al-Amin95

## Note

This repository is part of an academic dissertation. Results are reported only after
experiments are actually run; no results are claimed in advance.
