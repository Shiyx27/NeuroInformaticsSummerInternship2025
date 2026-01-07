# Security Auditing and Malicious Client Blocking in Federated EEG Seizure Detection

[![Conference](https://img.shields.io/badge/ICCIDS-2026-blue)](http://www.iccids.in/)
[![Framework](https://img.shields.io/badge/PyTorch-Federated-orange)](https://pytorch.org/)
[![Paper](https://img.shields.io/badge/Paper-IEEE-red)](https://ieeexplore.ieee.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> **Official PyTorch Implementation** of the paper accepted at the **2026 9th International Conference on Computational Intelligence in Data Science (ICCIDS) - a total of 916 paper submissions, out of which 92 papers were accepted, resulting in an overall acceptance rate of 10.26%**.

**[Initial Literature Comparison & Related Papers](https://docs.google.com/spreadsheets/d/1QylLldsTCb7MK8T_AyKOko3v2ACbH1W_Yi-SA9vQa0Y/edit?usp=sharing)**

This repository contains the complete implementation of a **secure, Byzantine-resilient federated learning framework** for real-time epileptic seizure detection on resource-constrained edge devices (Raspberry Pi 5).

---

## System Demo
[**Watch Full System Demo Video**](https://github.com/user-attachments/assets/7aee39bb-5a1e-4a4b-9e82-2b485c89a025)

---

## Abstract

While federated learning (FL) enables privacy-preserving medical AI, its vulnerability to malicious clients who can corrupt diagnostic models hinders widespread clinical adoption. We address this critical security gap with a novel **three-tier framework** for EEG seizure detection. Our architecture integrates an ultra-strict, HMAC-SHA256 remote attestation protocol to continuously verify and block untrusted clients in real-time, thereby safeguarding a federated network of lightweight CNNs deployed on resource-constrained Raspberry Pi devices.

## Comical Abstract
Self drawn using sketchbook
![3TierArchiComic](https://github.com/user-attachments/assets/6864f8c6-d507-4a6a-9a5e-5b3c181d4e50)

---
### Key Achievements
- **95.2%** diagnostic accuracy maintained even with **30% malicious clients** (vs 97.5% baseline)
- **98.7%** attack detection rate through zero-tolerance attestation
- **<15 ms** real-time inference on Raspberry Pi 5
- **0.54 MB** ultra-lightweight model (847K parameters)

---

## Three-Tier Architecture

Our framework defends against **model poisoning**, **data inference attacks**, and **Byzantine threats** using three dedicated security tiers:

### Tier 1: Edge Training
- Local EEG processing and seizure detection on Raspberry Pi devices
- Lightweight 1D-CNN optimized for ARM architecture
- Complete data privacy (raw EEG never leaves the device)

### Tier 2: Security Auditing
- **Zero-Tolerance Remote Attestation** using HMAC-SHA256 challenge-response protocol
- Real-time behavioral anomaly detection (cosine similarity, loss deviation)
- Dynamic trust scoring with permanent banning mechanism
- Average attestation time: **18.7 ms per client**

### Tier 3: Secure Aggregation
- Trust-weighted FedAvg excluding blocked clients
- Multi-layer encryption pipeline (AES-256 Fernet + TLS 1.3)
- Zlib compression for bandwidth optimization
- Tamper detection via SHA-256 HMAC verification

---

## Performance Metrics

### Clinical Performance
| Metric | Single Device | Federated (No Attack) | Federated (30% Attack) |
|:-------|:-------------:|:---------------------:|:----------------------:|
| **Accuracy** | 98.86% | 97.5% | **95.2%** |
| **Sensitivity** | 99.43% | 96.8% | **93.8%** |
| **Specificity** | 98.40% | 97.9% | **95.9%** |
| **F1-Score** | 99.0% | 0.96 | **0.93** |

### Security Performance
| Metric | Value | Description |
|:-------|:-----:|:------------|
| **Attestation Success Rate** | 99.2% | Successful challenge-response |
| **Attack Detection Rate** | 98.7% | Malicious clients identified |
| **Byzantine Tolerance** | 95.2% | Accuracy under 30% attack |
| **Blocked Clients** | 100% | Of detected malicious nodes |

### Edge Deployment
| Specification | Raspberry Pi 5 | Details |
|:--------------|:--------------:|:--------|
| **Model Size** | 0.54 MB | 847,234 parameters |
| **Inference Time** | <15 ms | Real-time capable |
| **Memory Usage** | 512 MB | Docker constrained |
| **Batch Size** | 8-16 | Dynamic adjustment |

---

## Getting Started

### Prerequisites
* Python 3.8+
* PyTorch 2.0+
* Raspberry Pi 4/5 (for edge deployment) or Linux PC (for simulation)
* CUDA 11.7+ (optional, for GPU training)
* Docker 20.10+ (for Raspberry Pi deployment)
* Linux (for simulation of 25 clients)


### Installation
```bash
git clone https://github.com/Shiyx27/NeuroInformaticsSummerInternship2025.git
cd NeuroInformaticsSummerInternship2025
pip install -r requirements.txt
```



## Dataset Information

### CHB-MIT Scalp EEG Database
- **Source:** [PhysioNet](https://physionet.org/content/chbmit/1.0.0/)
- **Subjects:** 24 pediatric patients with intractable seizures
- **Channels:** 23 EEG electrodes
- **Sampling Rate:** 256 Hz
- **Window Size:** 4 seconds (1024 samples)
- **Total Samples:** 11,000+ labeled windows
- **Split:** 70% Train / 15% Validation / 15% Test (subject-wise)

## Authors

| Name | Affiliation | Role | Contact |
|:-----|:------------|:-----|:--------|
| **Shiyamaladevi R S** | School of Electronics Engineering, VIT Chennai | Lead Developer | shiyamaladevirs@gmail.com |
| **Jeetashree Aparajeeta** | Center for NeuroInformatics, VIT Chennai | Research Advisor | jeetashree.a@vit.ac.in |
| **Swaroop S Kaimal** | School of Electronics Engineering, VIT Chennai | Co-Developer | swaroopskaimal@gmail.com |

---



## Citation

If you use this code or framework in your research, please cite our paper:
- **Will update the IEEE paper citation once published** Meanwhile,

-Shiyamaladevi R S, Swaroop S Kaimal, Jeetashree Aparajeeta. Security Auditing and Ultra-Strict Malicious Client Blocking in Federated EEG Seizure Detection. TechRxiv. November 14, 2025.

-DOI: 10.36227/techrxiv.176315562.27293302/v1

---

*Developed during the Summer 2025 NeuroInformatics Research Internship at Center For Neuroinformatics ,Vellore Institute of Technology.*

**Star this repository if you find it useful for your research!**
