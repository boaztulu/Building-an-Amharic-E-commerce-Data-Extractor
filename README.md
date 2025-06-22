# 🚀 EthioMart Amharic E-Commerce Data Extractor

> **A unified pipeline** to scrape, preprocess, and extract key entities from Ethiopian Telegram-based e-commerce channels using cutting-edge NLP techniques.

---

![Project Diagram](./docs/architecture.png)  
*Figure: High-level architecture showing Telegram ingestion → preprocessing → NER model → downstream analytics.*

---

## 📖 Table of Contents

1. [🎯 Project Overview](#-project-overview)  
2. [🛠️ Features](#️-features)  
3. [⚙️ Installation & Setup](#️-installation--setup)  
4. [📦 Project Structure](#-project-structure)  
5. [🚀 Usage](#-usage)  
   1. [Task 1: Data Ingestion](#task-1-data-ingestion)  
   2. [Task 2: CoNLL Labeling](#task-2-conll-labeling)  
   3. [Task 3: Fine-Tune NER](#task-3-fine-tune-ner)  
6. [📊 Sample Outputs](#-sample-outputs)  
7. [🔧 Configuration](#-configuration)  
8. [📈 Performance & Metrics](#-performance--metrics)  
9. [🤝 Contributing](#-contributing)  
10. [📜 License](#-license)  

---

## 🎯 Project Overview

EthioMart aims to **centralize** all Ethiopian Telegram-based e-commerce channels into one platform. This repo provides:

- **Real-time scraping** of product posts (text & images) from Telegram channels  
- **Amharic text cleaning** & normalization  
- **CoNLL-format** labeling of key entities (Product, Price, Location)  
- **Fine-tuning** of a multilingual transformer (XLM-RoBERTa) for Amharic NER  
- **Model explainability** via SHAP & LIME  
- **Vendor Scorecard** generation for micro-lending insights  

---

## 🛠️ Features

- ✅ **Asynchronous Telegram Scraper**  
- 🧹 **Robust Amharic Text Cleaner**  
- ✍️ **Manual & Automated CoNLL Labeling**  
- 🤖 **Transformer-based NER Fine-tuning**  
- 🔍 **Evaluation Metrics**: Precision, Recall, F1, Accuracy  
- 📊 **Interpretability**: SHAP & LIME visualizations  
- 💳 **Vendor Analytics Engine**: Posting frequency, views, lending score  

---

## ⚙️ Installation & Setup

```bash
# Clone the repo
git clone https://github.com/yourorg/EthioMart-Data-Extractor.git
cd EthioMart-Data-Extractor

# (Optional) Create & activate venv
python3 -m venv .venv && source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

├── README.md
├── requirements.txt
├── scripts/
│   ├── scrape_telegram.py       # Task 1: Async scraper
│   ├── text_cleaner.py          # Amharic normalization utilities
│   ├── label_conll.py           # Task 2: CoNLL dataset creator
│   ├── train_ner.py             # Task 3: NER fine-tuning
│   └── vendor_scorecard.py      # Task 6: Lending score engine
├── data/
│   ├── channels_to_crawl.xlsx   # Channel list
│   ├── processed_telegram_messages.csv
│   └── labeled_conll.txt
├── models/
│   └── xlm-roberta-ner/         # Saved fine-tuned model
├── notebooks/
│   ├── 01_data_ingestion.ipynb
│   ├── 02_labeling.ipynb
│   └── 03_training_and_eval.ipynb
└── docs/
    ├── architecture.png
    ├── sample_shap.png
    └── sample_lime.png
python scripts/scrape_telegram.py \
  --channels data/channels_to_crawl.xlsx \
  --limit 1000 \
  --out data/processed_telegram_messages.csv

scraper:
  limit: 1000
  media_dir: photos/

training:
  model_checkpoint: xlm-roberta-base
  epochs: 3
  train_batch: 8
  eval_batch: 8
