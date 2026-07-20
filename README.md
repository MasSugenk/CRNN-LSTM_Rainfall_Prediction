# Rainfall Prediction using Optimized Attention-CNN-LSTM

This repository contains the official implementation of the paper:  
**"Optimasi Model CNN-Attention untuk Prediksi Curah Hujan Mikro-Skala Menggunakan Data Sensor Lokal".**
 Previously, this research began with the development of local sensors with calibrated sensor devices and components and the research was published in the accredited journal Sinta.

## 📄 Paper 1
- Authors: Sugeng, Taufiq Nuzwir Nizar , Didit Andri Jatmiko, Rodi Hartono, Yusrila Yeka Kerlooza
- Journal: KOMPUTIKA
- DOI: (https://doi.org/10.34010/komputika.v13i2.13949 )

## 🏗️ Model Architecture
The proposed model combines:
- **Dilated CNN** (dilation_rate=2) to replace MaxPooling, preserving 5-minute temporal resolution
- **LSTM** for long-term temporal dependencies
- **Multi-Head Attention** (8 heads, key_dim=32) for dynamic feature weighting
- **Circular Time Features** (sin/cos of diurnal cycle) for day-night pattern recognition
- **Residual Connections** for training stability

## 📊 Results
| Model | Accuracy | Precision | Recall | F1-Score | ROC AUC |
|-------|----------|-----------|--------|----------|---------|
| Baseline CNN-LSTM | 69.05% | 17.54% | 74.97% | 0.3756 | 0.7638 |
| Attention-CNN-LSTM | 86.21% | 31.08% | 56.04% | 0.3998 | 0.8161 |
| **Optimized (Ours)** | **87.27%** | **32.27%** | **50.32%** | **0.3932** | **0.8239** |

- False positives reduced from 978 → 831 cases
- Optimal decision threshold: 0.80

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- TensorFlow 2.x

### Installation
```bash
git clone https://github.com/MasSugenk/CRNN-LSTM_Rainfall_Prediction.git
cd CRNN-LSTM_Rainfall_Prediction
pip install -r requirements.txt
```
## Training
```bash
python src/train.py --config configs/config.yaml
```
## Evaluation
```bash
python src/evaluate.py --model_path results/models/best_model.h5
```

