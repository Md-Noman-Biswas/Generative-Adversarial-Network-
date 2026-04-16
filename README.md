# Noise-Robust Gallbladder Ultrasound Image Classification using GAN-ViT

## 📌 Overview
This project presents a **noise-robust framework for gallbladder ultrasound image classification** using a combination of:

- U-Net based GAN for image denoising
- Vision Transformer (ViT) for classification

The system is designed to handle **real-world noisy ultrasound images**, improving robustness and diagnostic reliability.

---

## 🧠 Key Idea
Ultrasound images suffer from:
- Speckle noise
- Low contrast
- Operator-dependent artifacts  

To address this, we propose:
> A **unified GAN + Vision Transformer pipeline** that first denoises images and then performs classification.

---

## ⚙️ Methodology

### 1. GAN-based Denoising
- Generator: **ResSE U-Net with attention**
- Discriminator: **Residual + Self-Attention network**
- Loss:
  - LSGAN (MSE)
  - MAE for reconstruction

### 2. Noise Simulation
We simulate real-world ultrasound degradation using:
- Speckle noise
- Gaussian noise
- Gaussian blur
- Salt & pepper noise

Controlled using **Noise Severity Score (NSS)**.

### 3. Training Strategy
- Adaptive discriminator training
- Gradient clipping for stability
- Multi-level noise training (low, medium, high)

---

## 📂 Dataset
- Gallbladder Ultrasound Dataset (multi-class)
- Split into:
  - Train
  - Validation
  - Test

---

## 📊 Results

| Model        | Accuracy (High Noise) | ROC-AUC |
|-------------|----------------------|--------|
| ViT Only    | 17.78%               | -      |
| GAN + ViT   | **54.28%**           | **0.97** |

✅ Significant improvement in noisy conditions  
✅ Strong robustness across noise levels  

---

## 🏗️ Model Architecture

### Generator
- U-Net backbone
- Residual SE blocks
- Attention gates
- Skip connections

### Discriminator
- Residual blocks
- Self-attention layer
- Patch-based classification

---

## 🚀 Training Details
- Image size: 224×224
- Batch size: 32
- Epochs: 40
- Optimizer: Adam
- Loss:
  - Generator: MSE + MAE
  - Discriminator: MSE

---

## 📈 Evaluation Metrics
- Accuracy
- ROC-AUC
- PSNR (Peak Signal-to-Noise Ratio)
- SSIM (Structural Similarity Index)

---

## 📁 Project Structure
📦 project/
┣ 📜 notebook.ipynb
┣ 📜 model_summary.txt
┣ 📜 results.csv
┣ 📁 models/
┣ 📁 figures/
┗ 📜 README.md


---

## 🔬 Key Contributions
- Unified **GAN-ViT pipeline**
- Robust classification under heavy noise
- Systematic evaluation using **NSS**
- Improved performance over ViT-only baseline

---

## ⚠️ Limitations
- High computational cost
- Limited to single dataset
- Needs validation on real clinical environments

---

## 🔮 Future Work
- Multi-center clinical validation
- End-to-end optimization
- Explore diffusion-based denoising
- Real-time deployment optimization

---

## 🧑‍💻 Author
**Md. Noman Biswas Sibly**  
Rajshahi University of Engineering & Technology (RUET)

---

## 📜 License
This project is for academic and research purposes.

---

## ⭐ Acknowledgment
Based on research in:
- GAN-based denoising
- Vision Transformers
- Medical image analysis  
