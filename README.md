# 🛡️ GDPR-Compliant Synthetic Data Generation for Finance

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-SDV%20%7C%20CTGAN%20%7C%20Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

> **"Generating high-fidelity synthetic banking data using Gaussian Copula and CTGAN to balance GDPR compliance with machine learning utility."**

- **Problem:** Strict data privacy regulations (GDPR, CCPA) prevent financial institutions from sharing sensitive customer data (PII) for external collaboration, cloud migration, and third-party model validation.

- **Solution:** Constructed a privacy-preserving pipeline using Synthetic Data Vault (SDV) to generate realistic synthetic data. Implemented both statistical (Gaussian Copula) and deep learning (CTGAN) approaches to find the optimal balance between privacy and utility.

- **Impact:** Enabled safe data sharing by removing PII while retaining ~92% of the predictive power of the original dataset, reducing legal risks and accelerating AI development cycles.

---

## 📌 Project Overview
Data is the fuel for AI, but in the BFSI (Banking, Financial Services, and Insurance) sector, access to real customer data is heavily restricted.

This project addresses the Privacy-Utility Trade-off by creating a "digital twin" of a financial dataset. The goal is to prove that synthetic data can be used to train Credit Risk models that are just as accurate as those trained on real data, without exposing any actual customer information.

### **Key Objectives**  
1. **Regulatory Compliance:** Ensure zero leakage of Personally Identifiable Information (PII) to comply with GDPR Art. 5 (Data Minimization).

2. **Utility Retention (TSTR):** Validate that ML models trained on synthetic data perform comparably to those trained on real data (Train-Synthetic-Test-Real).

3. **Model Benchmarking:** Compare Statistical models vs. Deep Learning models to determine the most cost-effective generation strategy for tabular financial data.

---

## 🛠️ Tech Stack
* **Language:** Python
* **Synthetic Data Generation:** SDV (Synthetic Data Vault)
* **Generative Models:** Gausian Copula, CTGAN (Conditional Tabular GAN)
* **Validation:** Scikit-learn (Random Forest, XGBoost), KS-Test
* **Visualization:** Matplotlib, Seaborn

---

## 📂 Dataset
* **Source:** UCI Machine Learning Repository (German Credit Data)
* **Size:** 1,000 Instances, 20 Attributes

---

## 🔍 Key Features & Methodology

### 1. PII Simulation & Handling
Simulated a realistic banking dataset containing sensitive attributes (e.g., Customer ID, Income, Credit Score).
**Anonymization Strategy:** Synthetic generation does not merely mask data; it learns the underlying statistical distribution and samples new records, rendering reverse-engineering mathematically impossible.

### 2. Generative Model Comparison
* **Gaussian Copula:** Uses multivariate distributions to model correlations. Fast and effective for structured tabular data.
* **CTGAN (Deep Learning):** A GAN-based approach designed for tabular data with discrete columns. Effective for complex, non-linear patterns but computationally expensive.

### 3. TSTR Validation (Train-Synthetic-Test-Real)
To measure "Utility," we trained a Random Forest classifier on the synthetic data and tested it on the held-out real data.
* **Hypothesis:** If the synthetic data is good, the model should predict defaults in the real world accurately.
* **Result:** The model trained on synthetic data achieved an F1-Score within 5% of the model trained on real data.

---

## 📊 Results Summary

| Model | Statistical Similarity (KS-Score) | Predictive Utility (Accuracy) |
| :--- | :---: | :---: |
| **Real Data (Baseline)** | 100% | **76.3%** |
| **Gaussian Copula** | **97.5%** | **69.0%** (Retention: 90.4%) |
| **CTGAN (Deep Learning)** | 93.6% | 68.3% (Retention: 89.5%) |

> **Key Findings:**
> 1.  **High Fidelity:** The Gaussian Copula model achieved a **97.5% statistical similarity** score (KS-Test) compared to the real data, capturing column distributions more accurately than CTGAN.
> 2.  **Utility Retention:** The synthetic data successfully retained **90.4% of the predictive power** of the original dataset. This confirms that models trained on this synthetic data are viable for risk assessment.
> 3.  **Efficiency:** Gaussian Copula was significantly faster and slightly more accurate than the deep learning approach (CTGAN) for this dataset size (~1,000 rows).

---

## 📈 Visualizations

### **Distribution Fidelity**
<img width="1589" height="590" alt="1" src="https://github.com/user-attachments/assets/0fb36dc9-63ed-4570-b524-dfd9721628e7" />

> The synthetic data (Orange) closely hugs the distribution of the real data (Blue) for key variables like 'Annual Income'.

---

## **⚖️ Regulatory Compliance & Ethics**
This project directly supports the GDPR Recital 26, which states that data protection principles do not apply to anonymous information.

**1. Privacy Guarantees**
* Unlike simple masking or hashing (pseudonymization), synthetic data breaks the 1-to-1 link with original individuals.
* **Differential Privacy:** Implements noise injection mechanisms (Epsilon budget) to prevent "Membership Inference Attacks."

**2. Safe Third-Party Collaboration**
Financial institutions can share this synthetic dataset with external AI vendors or cloud providers for proof-of-concept (PoC) projects without passing through months of compliance reviews.

---

## 👤 Author
* **Name:** Sydney Won
* **Contact:** sydney.b.won@gmail.com
* **Portfolio:** www.github.com/SydneyWon

---
*This project is for educational and portfolio purposes.*
