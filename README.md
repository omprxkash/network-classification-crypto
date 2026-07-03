# Network Traffic Classification — Encrypted & Crypto Protocols

ML-based classification of encrypted network traffic and cryptocurrency protocol flows using packet-level feature engineering, without decryption. Built as a data analysis project at VIT Chennai.

## The Challenge

You can't inspect encrypted payloads — but you can still learn a lot from the metadata. Packet size patterns, timing between packets, flow duration, byte ratios between source and destination: these fingerprint a protocol even when the content is hidden. This project builds that feature set and compares classifiers on it.

## Dataset

**UNSW-NB15 Network Traffic Dataset**
- 82,332 training samples, 45 features
- Protocol types: TCP, UDP, ICMP, ARP
- Services: HTTP, DNS, FTP, SSH, and others
- Attack categories: DoS, Probe, R2L, U2R, and Normal traffic
- 40 numeric features + 4 categorical (one-hot encoded)
- Preprocessing: outlier clamping at 95th percentile, log transformation for skewed distributions, dropped low-frequency protocols

## Features Engineered

- Packet size distributions (min, max, mean, variance)
- Inter-arrival timing patterns
- Flow duration and byte counts
- Source-to-destination byte ratios
- Protocol type and service fingerprints
- TTL, window size, jitter statistics

## Results

| Model | Accuracy |
|---|---|
| **Random Forest** | **97.65%** |
| KNN (k=3) | ~97% |
| XGBoost | 94.9% |
| Decision Tree | — |

Random Forest confusion matrix: TN=7253, FP=147, FN=240, TP=8827  
Precision: 0.98 · Recall: 0.97 · F1: 0.98

## Repository Contents

| File | Description |
|---|---|
| `c3crypto (1).ipynb` | Feature engineering pipeline, model training, evaluation |
| `CRYPTO_REPORT_DA3.pdf` | Final project report |
| `CRYPTO_REPORT_FINAL.pdf` | Reviewed final report |
| `crypto_ppt_reportda3.pptx` | Presentation slides |

## Stack

Python · scikit-learn · XGBoost · pandas · Jupyter Notebook
