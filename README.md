# GAN-based Ultrasound Image Denoising (ResSE U-Net + Attention)

## Overview
This implementation trains a **GAN-based denoising model** for ultrasound images.  
The generator is a **ResSE U-Net with attention**, and the discriminator uses **residual blocks with self-attention**.

---

## Features
- U-Net generator with:
  - Residual SE (Squeeze-and-Excitation) blocks
  - Attention gates
  - Skip connections
- Discriminator with:
  - Residual blocks
  - Self-attention mechanism
- Noise simulation:
  - Speckle noise
  - Gaussian noise
  - Gaussian blur
  - Salt & pepper noise
- Evaluation using:
  - PSNR
  - SSIM

---

## Dataset
Dataset directory structure:


Images are automatically loaded and preprocessed.

---

## Training Details
- Image size: 224×224
- Batch size: 32
- Epochs: 40
- Optimizer: Adam
- Loss:
  - GAN loss: MSE (LSGAN)
  - Reconstruction loss: MAE

---

## Workflow
1. Load and preprocess images
2. Add synthetic noise (low / medium / high)
3. Train GAN:
   - Train discriminator
   - Train generator
4. Validate using PSNR and SSIM
5. Save:
   - Model checkpoints
   - Training plots
   - Sample outputs

---

## Output
During training:
- Denoised image samples are generated per epoch
- PSNR and SSIM are calculated
- Models are saved (`.keras` format)

---

## Key Components

### Generator
- Function: `build_medical_res_se_unet()`
- Architecture:
  - Encoder-decoder (U-Net)
  - Residual SE blocks
  - Attention-based skip connections

### Discriminator
- Function: `build_discriminator()`
- Architecture:
  - Residual blocks
  - Self-attention layer
  - Patch-based output

---

## Metrics
- **PSNR (Peak Signal-to-Noise Ratio)**
- **SSIM (Structural Similarity Index)**

---

## Notes
- Instance Normalization is used if available, otherwise Batch Normalization
- Gradient clipping is applied for stable GAN training
- Adaptive discriminator training is used for better convergence
