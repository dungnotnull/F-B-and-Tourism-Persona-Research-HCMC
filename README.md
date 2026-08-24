# F&B and Tourism Persona Research (HCMC)

This repository contains the source code, experimental notebooks, and evaluations for a research project on customer segmentation (personas) in the Food & Beverage (F&B) and Tourism sectors in Ho Chi Minh City (HCMC). The study focuses on building an automated pipeline for classifying and retrieving customer personas using various Natural Language Processing (NLP) and Large Language Models (LLMs).

## Project Overview

The project is structured around several core experiments to evaluate the effectiveness of different language models in a weak labeling and information retrieval setting. We compare traditional cross-lingual models against modern LLMs for zero-shot and few-shot classification tasks.

### Key Components

- **Weak Labeling Pipelines (Versions A, B, C):**
  Three distinct iterations of weak labeling models were evaluated on a unified set of personas:
  - **Version A (`verA.ipynb`):** Uses XLM-R-XNLI.
  - **Version B (`verB.ipynb`):** Uses mDeBERTa-XNLI.
  - **Version C (`verC.ipynb`):** Uses Google's Gemini 3.5 Flash-Lite via API.
  
- **Unified Gold Validation (`unified_gold_validation.ipynb`):**
  A centralized evaluation script that computes Cohen's Kappa scores to measure the agreement between the generated weak labels (from all three models) and a manually curated set of 300 "gold" labels.
  
- **Retrieval Evaluation (`retrieval_evaluation.ipynb` / `retrieval_evaluation_v3.ipynb`):**
  Experiments assessing the retrieval performance of the generated persona vectors compared to random baselines.

- **Dashboard Mockup (`dashboard_fnb_persona_mockup.html`):**
  An interactive HTML/JS mockup of the proposed dashboard used to visualize the F&B and Tourism personas and provide actionable insights.

## Repository Structure

```
├── .gitignore                           # Git ignore configurations
├── verA.ipynb                           # XLM-R Weak Labeling Pipeline
├── verB.ipynb                           # mDeBERTa Weak Labeling Pipeline
├── verC.ipynb                           # Gemini 3.5 Weak Labeling Pipeline
├── unified_gold_validation.ipynb        # Cohen's Kappa evaluation against 300 gold labels
├── retrieval_evaluation_v3.ipynb        # Retrieval pipeline and evaluation
├── dashboard_fnb_persona_mockup.html    # Interactive F&B Persona Dashboard Mockup
├── *.csv / *.xlsx                       # Checkpoints, raw data, and kappa/retrieval results
└── *.png                                # Evaluation charts (e.g., F1 scores, Kappa, Retrieval benchmarks)
```

*(Note: Research drafts and `.docx` manuscripts are ignored via `.gitignore` and are not included in the remote repository).*

## Setup & Execution

### Prerequisites
- Python 3.8+
- Jupyter Notebook
- Required Python libraries (can be found within the respective `.ipynb` files, such as `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `google-genai`, etc.)

### Running the Gemini Pipeline (Version C)
If you intend to run `verC.ipynb` or `unified_gold_validation.ipynb`, you must provide a valid Gemini API Key:
```bash
export GEMINI_API_KEY="your_api_key_here"
```

## Results & Visualizations
The output figures (like `hinh3_microf1_by_pipeline.png` and `unified_kappa_per_label.png`) showcase the comparative performance of the models across various persona labels. Gemini 3.5 Flash-Lite (Version C) generally demonstrates distinct behavior in weak labeling distributions when compared to earlier BERT-based iterations.
