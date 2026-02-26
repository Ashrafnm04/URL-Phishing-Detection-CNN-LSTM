# URL-Phishing-Detection-CNN-LSTM

A hybrid deep learning framework for malicious URL detection, utilizing **CNN-LSTM** architecture and advanced domain-level aggregation strategies: **SPhS**, **MSS**, and **WeAS**.

## 🛡️ Project Overview
This project presents a robust, AI-driven framework for detecting phishing threats by analyzing URL character sequences and metadata. Developed as part of my **Master in Information Security at Universiti Putra Malaysia (UPM)**, this research moves beyond simple binary classification by implementing advanced Domain-Level Decision Strategies to account for webpage contextual relationships.

## ⚠️ The Problem Statement
Traditional detection methods often fail because they examine URLs independently (atomic analysis). They disregard the structural and contextual relationships within webpage architecture, allowing sophisticated phishing campaigns to evade detection by hiding malicious payloads in specific sub-components (scripts/iframes).

## 🎯 The Objective
To develop a hybrid architecture that:
1. Extracts spatial features and n-gram patterns using **CNN**.
2. Learns sequential character dependencies using **LSTM**.
3. Enhances binary classification through **domain-level decision strategies** that leverage webpage context for more accurate threat intelligence.

## 🏗️ Model Architecture

The model pipeline follows:
**Embedding Layer** ➔ **Conv1D Layer** ➔ **GlobalMaxPooling** ➔ **LSTM** ➔ **Dense/Dropout** ➔ **Decision Strategies**

## 🧠 Summary of Decision Strategies
| Strategy | Logic | Use Case |
| :--- | :--- | :--- |
| **Single Phishing (SPhS)** | If *any* URL in the webpage is classified as phishing, the entire domain is flagged. | High-security, zero-tolerance environments. |
| **Mean Sum (MSS)** | Uses the average prediction score of all URLs. If the mean exceeds a threshold, it is phishing. | Balanced detection for general web filtering. |
| **Weighted Average (WeAS)** | Assigns specific weights to URLs based on location (e.g., Script > Anchor). Higher scores flag the domain. | **Optimized for modern, complex web threats.** |

## 📊 Model Results
| Model Strategy | Accuracy% | Precision% | Recall% | F1-score% |
| :--- | :---: | :---: | :---: | :---: |
| CNN-LSTM (Base) | 92.80 | 86.10 | 69.30 | 76.80 |
| CNN-LSTM + SPhS | 89.19 | 87.02 | 91.68 | 89.29 |
| CNN-LSTM + MSS | 93.73 | 93.64 | 93.60 | 93.62 |
| **CNN-LSTM + WeAS** | **93.92** | **93.64** | **94.00** | **93.82** |

## 🏁 Conclusion
The implementation of domain-level strategies significantly improves detection performance over base models. Specifically, the **Weighted Average Strategy (WeAS)** provided the best balance, achieving a **94.00% Recall** and **93.82% F1-score**, proving that location-aware weighting is critical for identifying obfuscated phishing attempts.