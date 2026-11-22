# DNS Exfiltration Detection — LightGBM Model

## Project Overview
A machine learning-based Intrusion Detection System (IDS) that detects DNS data exfiltration attacks using a LightGBM binary classifier.

## Model Performance
- **AUC: 1.0000** on held-out test set
- Zero false positives, zero false negatives
- Live lab test: scored 0.80–0.81 against real dnscat2 attack traffic

## Approach
- **Algorithm:** LightGBM gradient boosting
- **Split:** 60% train / 20% validation / 20% test
- **Features:** 29 flow-based features (TTL statistics, packet sizes, domain entropy, etc.)
- **Top signal:** TTL behavior explains 55.8% of model gain

## Files
| File | Description |
|---|---|
| `Lightgmb_validation.ipynb` | Full training pipeline — data loading, split, training, evaluation |
| `dns_lgbm_model_v2.txt` | Trained LightGBM model (native .txt format) |
| `confusion_matrix_v2.png` | Test set confusion matrix |
| `feature_importance_final.png` | Feature importance heatmap |

## Dataset
DNS Exfiltration Dataset — flow-based features from dnscat2, iodine, cobaltStrike, dns2tcp, and benign traffic.

## Live Testing
Deployed on an IDS VM and tested against real dnscat2 attack in a lab environment (Kali attacker → Ubuntu victim). Model correctly flagged all attack traffic.
