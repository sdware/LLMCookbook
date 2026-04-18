# LLM Workshop — Three-Stage Pipeline

A complete, end-to-end example covering the three stages of a practical NLP / LLM workshop.
The running task is **sentiment classification** (positive / negative / neutral).

## Notebooks

| Notebook | Stage | Key libraries |
|---|---|---|
| `notebook_01_annotation.ipynb` | Data annotation | pandas, scikit-learn |
| `notebook_02_prompting.ipynb` | Local LLM prompting & eval | Ollama, requests, scikit-learn |
| `notebook_03_finetuning.ipynb` | Fine-tuning & re-evaluation | transformers, datasets, torch |

## Data flow

```
notebook_01  →  annotated_dataset.jsonl
notebook_02  →  evaluation_results_stage2.csv, metrics_summary_stage2.csv
notebook_03  →  finetuned_sentiment_model/,   stage3_comparison.png
```

## Setup

```bash
# Core dependencies
pip install pandas scikit-learn requests matplotlib seaborn \
            transformers datasets torch

# For notebook 2 (local LLM)
# 1. Install Ollama: https://ollama.ai/download
# 2. Pull model:   ollama pull mistral
# 3. Start server: ollama serve
```

## How to run

Run notebooks **in order**: 01 → 02 → 03.
Each notebook reads outputs from the previous stage.

## Swapping models

- **Notebook 02**: change `MODEL_NAME = 'mistral'` to any model installed via Ollama
  (e.g. `llama3`, `phi3`, `gemma2`).
- **Notebook 03**: change `MODEL_CHECKPOINT = 'distilbert-base-uncased'` to any
  HuggingFace sequence-classification model.
