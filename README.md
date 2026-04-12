# 🛡️  IntrusionIQ — AI-Powered Network Intrusion Detection System

> B.Tech Cybersecurity Capstone Project | Sri Sri University | 2026

![Python](https://img.shields.io/badge/Python-3.10-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4+-orange)
![Streamlit](https://img.shields.io/badge/Streamlit-1.32+-red)
![Accuracy](https://img.shields.io/badge/Accuracy-98.84%25-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 📌 Overview

IntrusionIQ is a machine learning-powered Network Intrusion Detection System
(NIDS) that detects and classifies 12 types of network attacks in near
real-time. Built on the CICIDS2017 benchmark dataset, the system achieves
98.84% classification accuracy using a Random Forest classifier.

## 🎥 Demo

![Dashboard Demo](docs/dashboard_preview.png)

## ✨ Features

- **98.84% accuracy** on CICIDS2017 test data
- **12 attack type detection** — DDoS, DoS Hulk, PortScan, FTP-Patator,
  SSH-Patator, Web Attacks, Infiltration and more
- **Real-time simulation engine** at 50 packets/second
- **Live Streamlit dashboard** with attack visualization and alert log

- **3-VM attack laboratory** using Kali Linux and Metasploitable 2
- **Hybrid detection system** — synchronized real attack execution with
  dashboard detection

## 🏗️  System Architecture

CICIDS2017 Dataset (CSV)
↓
[ Preprocessing Pipeline ]  ← clean, normalize, encode, SMOTE balance
↓
[ Feature Selection ]       ← top 20 features from 79
↓
[ Random Forest Model ]     ← 98.84% accuracy, F1 weighted 0.99
↓
[ Simulation Engine ]       ← 50 packets/sec, SQLite logging
↓
[ Streamlit Dashboard ]     ← live charts, alert table, attack detection

## 📊 Model Performance

| Model | Accuracy | F1 Macro | F1 Weighted |
|---|---|---|---|
| Random Forest (Primary) | 98.84% | 0.7207 | 0.99 |
| Decision Tree | 97.94% | 0.7210 | 0.98 |
| Logistic Regression | 65.47% | 0.3019 | 0.71 |

## 🛠️  Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.10 |
| ML | scikit-learn, imbalanced-learn (SMOTE) |
| Data | pandas, numpy |
| Dashboard | Streamlit, Plotly |
| Database | SQLite3 |
| Visualization | matplotlib, seaborn |
| Attack Lab | VMware, Kali Linux, Metasploitable 2 |
| OS | Ubuntu 22.04 LTS |

## 📁 Project Structure


IntrusionIQ/
├── data/
│   ├── cicids2017/          # CICIDS2017 CSV files (not included - download separately)
│   ├── X_test_scaled.npy    # Preprocessed test features
│   └── y_test.npy           # Test labels
├── models/
│   ├── rf_model.pkl         # Trained Random Forest model
│   ├── scaler.pkl           # StandardScaler
│   ├── label_encoder.pkl    # LabelEncoder
│   └── top_features.json    # Selected feature names
├── notebooks/
│   ├── 01_eda.ipynb         # Exploratory Data Analysis
│   ├── 02_preprocessing.ipynb  # Data cleaning and SMOTE
│   └── 03_training.ipynb    # Model training and evaluation
├── src/
│   ├── simulate.py          # Simulation engine
│   └── attack_trigger.py   # Hybrid attack trigger system
├── dashboard/
│   └── app.py               # Streamlit dashboard
├── docs/
│   ├── confusion_matrix_rf.png
│   ├── class_distribution.png
│   └── correlation_heatmap.png
├── logs/                    # SQLite alerts database (auto-created)
├── requirements.txt
└── README.md

## ⚙️ Installation and Setup

### Prerequisites
- Ubuntu 22.04 LTS
- Python 3.10+
- 8 GB RAM minimum

### Step 1 — Clone the repository

```bash
git clone https://github.com/theconsoler/IntrusionIQ.git
cd IntrusionIQ
```

### Step 2 — Create virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 3 — Install dependencies

```bash
pip install -r requirements.txt
```

### Step 4 — Download CICIDS2017 Dataset

Download from:
https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset

Place all 8 CSV files in `data/cicids2017/`

### Step 5 — Run Preprocessing and Training

```bash
# Open Jupyter and run notebooks in order
jupyter notebook notebooks/01_eda.ipynb
jupyter notebook notebooks/02_preprocessing.ipynb
jupyter notebook notebooks/03_training.ipynb
```

### Step 6 — Run the System

**Terminal 1 — Start simulation:**
```bash
cd src
source ../venv/bin/activate
python simulate.py
```

**Terminal 2 — Start dashboard:**
```bash
cd dashboard
source ../venv/bin/activate
streamlit run app.py
```

Open browser → `http://localhost:8501`

## 🔬 Attack Laboratory

The project includes a three-VM isolated attack lab:

| VM | Role | IP |
|---|---|---|
| Ubuntu 22.04 | NIDS Detector | 192.168.100.10 |
| Kali Linux | Attacker | 192.168.100.20 |
| Metasploitable 2 | Victim | 192.168.100.30 |

Attack types demonstrated: nmap port scan, hping3 DoS flood,
Hydra SSH brute force, Hydra FTP brute force, SQLmap SQL injection.

## 👥 Individual Work

- **Piyush Kumar Sahoo** — ML Engineer, Project Lead & Security work

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgements

- Canadian Institute for Cybersecurity (CIC) for the CICIDS2017 dataset
