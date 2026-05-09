# Engineering AI Frameworks for Real-Time Financial Fraud Detection: A Systematic Review

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![PRISMA 2020](https://img.shields.io/badge/Methodology-PRISMA%202020-blue)]()
[![Studies Reviewed](https://img.shields.io/badge/Studies%20Reviewed-99-green)]()
[![Period](https://img.shields.io/badge/Period-2021--2025-orange)]()

> **D. Amaral** · **L. Faria**  
> Instituto Superior de Engenharia do Porto (ISEP), Porto, Portugal  
> Correspondence: [1160088@isep.ipp.pt](mailto:1160088@isep.ipp.pt) · ORCID: [0009-0004-0155-6817](https://orcid.org/0009-0004-0155-6817)

---

## Overview

This repository contains the manuscript and supplementary materials for a **PRISMA 2020-compliant systematic review** examining the use of Machine Learning (ML) and Artificial Intelligence (AI) for financial fraud detection. The review covers **99 peer-reviewed studies** published between **January 2021 and October 2025**, spanning card-based payments, online banking, e-commerce, blockchain transactions, and anti-money laundering.

The work develops a **structured taxonomy** of AI techniques, critically analyses evaluation methodologies and deployment challenges, and delineates a research agenda for next-generation, deployment-ready fraud detection systems.

---

## Highlights

- **Comprehensive PRISMA-compliant systematic review** of AI/ML frameworks for financial fraud detection (2021–2025), synthesising 99 primary studies selected from 1,124 initial records across Web of Science, ScienceDirect, and SpringerLink.
- **Structured taxonomy** categorising contemporary approaches into supervised, unsupervised, deep learning, graph-based, federated, and explainable AI (XAI) across transaction, entity, and network analysis levels.
- **Critical analysis** of cross-cutting technical challenges: extreme class imbalance, concept drift, adversarial robustness, and the growing demand for regulatory-aligned transparency.
- **Identification of a technological shift** from classical tree-based ensembles toward advanced architectures such as Transformers, Graph Neural Networks (GNNs), and privacy-preserving Federated Learning.

---

## Research Questions

| ID | Research Question |
|----|-------------------|
| **RQ1** | What categories of ML methods have been employed for detecting fraud in financial transaction systems since 2021, and how are they deployed across different data types and system architectures? |
| **RQ2** | How do these methods perform in terms of predictive accuracy, discrimination, and operational utility, and how robust are reported results to methodological choices such as dataset selection, handling of class imbalance, and prevention of data leakage? |
| **RQ3** | What methodological, technical, and regulatory challenges remain insufficiently addressed, and what future research directions emerge for constructing scalable, privacy-preserving, explainable, and adversarially robust fraud detection systems? |

---

## Methodology

The review follows **PRISMA 2020** guidelines with a pre-registered protocol.

### Search Strategy

Three bibliographic databases were queried:

- **Web of Science** — `("Fraud Detection") AND ("Artificial Intelligence" OR "Machine Learning") AND ("Challenges" OR "Techniques")`
- **ScienceDirect** — `("Finance" AND "Fraud Detection") AND ("Artificial Intelligence" OR "Machine Learning") AND ("Challenges" OR "Techniques")`
- **SpringerLink** — same as ScienceDirect

Filters: 2021–2025, English language, peer-reviewed journal articles and full conference papers.

### Selection Process

| Stage | Count |
|-------|-------|
| Records identified | 1,124 |
| Duplicates removed | 24 |
| Title/abstract screening — included | 397 |
| Title/abstract screening — excluded | 703 |
| Full-text reviewed | 397 |
| Full-text excluded | 298 |
| **Final studies included** | **99** |

Screening and deduplication were managed using **Zotero** and **Rayyan**.

### Eligibility Criteria (PEO Framework)

- **Population/Problem:** Financial transaction systems (card payments, online/mobile banking, e-commerce, blockchain).
- **Exposure/Intervention:** ML/AI methods for fraud detection — supervised, unsupervised, semi-supervised, deep learning, graph-based, federated, XAI, and hybrid/ensemble approaches.
- **Outcome:** At least one standard quantitative performance metric (accuracy, precision, recall, F1, AUC-ROC, PR-AUC, MCC, latency, etc.) with sufficient methodological detail.

---

## Taxonomy of AI Methods

The taxonomy is organised along three axes: **problem formulation**, **data modality**, and **model family**.

### Levels of Analysis

| Level | Description | Typical Methods |
|-------|-------------|-----------------|
| Transaction-level | Classify each transaction as fraudulent or legitimate | XGBoost, LightGBM, LSTM, CNN |
| Entity/account-level | Assign risk scores to accounts, customers, or merchants | VAEs, Isolation Forests, GNNs |
| Network-level | Detect fraud rings, collusive networks, money-laundering chains | GCN, GraphSAGE, GAT |

### Operational Regimes

- **Batch / near-real-time scoring** — periodic retraining, offline evaluation.
- **True real-time / streaming** — sub-50 ms decisions in card payment and online banking systems; requires lightweight architectures and feature pipelines.

### Model Families

| Family | Representative Models | Typical AUC-ROC | Notes |
|--------|-----------------------|-----------------|-------|
| Tree-based ensembles | XGBoost, LightGBM, CatBoost | 0.96 – 0.99 | De facto standard for tabular fraud data |
| Deep learning (tabular/sequential) | DCNN, LSTM, GRU, Transformer | 0.95 – 0.99 | Strong on sequential behavioural data |
| Graph-based | GCN, GraphSAGE, GAT, MetaFraud-GNN | 0.95 – 0.99 | Best for coordinated/network fraud |
| Federated & privacy-preserving | FedGAT-DCNN, FL-GNN | 0.97 – 0.999 | Cross-institution without raw data sharing |
| Unsupervised / anomaly detection | Autoencoder, VAE, Isolation Forest, GAN | — | Effective when labels are scarce or delayed |
| Explainable AI (XAI) | SHAP, LIME (post-hoc layers) | — | Cross-cutting; applied atop other models |
| Metaheuristic optimisation | GA, PSO, Differential Evolution | — | Feature selection and hyperparameter tuning |

---

## Key Findings

### Performance by Domain

| Domain | Top Models | Avg AUC-ROC | Main Datasets |
|--------|-----------|-------------|---------------|
| Credit card | XGBoost / LightGBM | 0.96 – 0.99 | European cardholder (Kaggle) |
| Blockchain | GNN / Federated | 0.97 – 0.99 | Elliptic / Ethereum |
| Online banking | CNN-LSTM | 0.95 – 0.98 | European (Kaggle-like) / Taiwan |

### Evaluation Metric Usage

- **Accuracy** and **AUC-ROC** dominate — but can be misleading under extreme class imbalance.
- **PR-AUC** is more informative yet under-reported relative to AUC-ROC.
- **Latency and throughput** benchmarks are largely absent despite their central role in real-time systems.
- **MCC** and cost-sensitive metrics appear in only a minority of works.

### Temporal Trends (2021–2025)

- Gradual shift from classical ML to **deep and graph-based architectures**.
- **Federated learning** gains prominence from 2023 onwards.
- **Explainable AI** transitions from a peripheral topic to a central research theme.
- More studies begin reporting PR-AUC and acknowledging concept drift by 2024–2025.

---

## Cross-Cutting Challenges

### 1. Extreme Class Imbalance
Fraud datasets can have imbalance ratios in the order of thousands to one. Widely used countermeasures include SMOTE variants, GANs/VAEs for synthetic oversampling, cost-sensitive learning, and focal loss. Evidence suggests that aggressive resampling can distort XAI feature attributions.

### 2. Concept Drift
Fraud patterns evolve continuously. Most studies use static train/test splits that ignore temporal dynamics, leading to overly optimistic performance estimates. Online learning, sliding windows, and periodic retraining protocols are proposed but rarely evaluated systematically.

### 3. Adversarial Robustness
Fraudsters adapt to detection mechanisms via evasion and data poisoning attacks. Adversarial robustness is rarely evaluated; no standard benchmark exists for this dimension in fraud detection.

### 4. Explainability & Governance
SHAP and LIME are the most common post-hoc explanation techniques. Local explanations justify individual alerts; global explanations support model governance and regulatory audits. The interaction between imbalance countermeasures and explanation stability remains an open research problem.

### 5. Privacy-Preserving & Federated Learning
Federated architectures enable cross-institutional training without raw data sharing. Key open challenges include handling non-IID data distributions, securing model updates against poisoning attacks, and achieving regulatory acceptance.

---

## Repository Structure

```
.
├── main.tex                  # Main LaTeX manuscript
├── main.bib                  # BibTeX reference database
├── figs/
│   └── prisma.png            # PRISMA 2020 flow diagram
├── supplementary/            # Search strategies, data extraction form, protocol
└── README.md
```

---

## Citation

If you use this work, please cite:

```bibtex
@article{amaral2025engineering,
  title   = {Engineering {AI} Frameworks for Real-Time Financial Fraud Detection: A Systematic Review},
  author  = {Amaral, Diogo and Faria, Luiz},
  journal = {(under review)},
  year    = {2025},
  note    = {ISEP, Porto, Portugal}
}
```

---

## Authors & Contributions

| Author | Affiliation | Contributions |
|--------|-------------|---------------|
| **Diogo Amaral** (corresponding) | ISEP, Porto, Portugal | Conceptualization, Methodology, Software, Formal Analysis, Investigation, Writing — original draft |
| **Luiz Faria** | ISEP, Porto, Portugal | Supervision, Conceptualization, Writing — review & editing |

---

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material for any purpose, provided appropriate credit is given.
