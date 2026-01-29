# Image Denoising Using Deep Learning (U-Net)  
_Deployed on AWS EC2 (Ubuntu 24.04)_

## Project Overview
This project implements a **deep learning–based image denoising system** using a **U-Net encoder–decoder architecture**.  
The trained model removes **synthetic noise** from natural images and is deployed as a **REST API** on an **AWS EC2 instance running Ubuntu 24.04**.

The project integrates concepts from:
- **Fundamentals of Machine Learning**
- **Artificial Intelligence**
- **Cloud Computing (AWS EC2)**
- **Model Deployment using FastAPI**

---

## Dataset Used
**BSDS500 (Berkeley Segmentation Dataset)**

- 500 natural images
- Train / Validation / Test split
- Images resized to **256 × 256**
- Clean–noisy image pairs created for supervised learning

### Noise Types
- Gaussian Noise (low, medium, high)
- Poisson Noise

---

## Data Preprocessing
- Images normalized to range **[0, 1]**
- Noise added synthetically using NumPy
- Paired clean and noisy datasets prepared for training
- Data fed into the U-Net model for image-to-image learning

---

## Model Architecture
- **U-Net–based encoder–decoder**
- Skip connections for spatial detail preservation
- Layers used:
  - Convolution
  - LeakyReLU
  - Batch Normalization
  - Dropout
- Output layer with **sigmoid activation**

**Total Parameters:** ~125 million

---

## Loss Functions
The model was trained using multiple loss functions:

1. **Mean Squared Error (MSE)**
2. **Structural Similarity Index (SSIM)**
3. **Hybrid Loss (SSIM + MAE)**  
Final Loss = 0.7 × SSIM Loss + 0.3 × MAE


---

## Training Details
- Optimizer: **Adam**
- Learning Rate: `1e-4`
- Batch Size: `8`
- Epochs: `100`
- Evaluation Metric: **SSIM**

### Final Performance
- **Test SSIM ≈ 0.74** (Hybrid Loss)

---

## Deployment on AWS EC2

### Cloud Environment
- **Cloud Provider:** Amazon Web Services (AWS)
- **Service:** EC2 (Elastic Compute Cloud)
- **Operating System:** Ubuntu **24.04 LTS**
- **Instance Type:** (e.g., t2.micro / t3.medium)

---

### Deployment Steps Summary
1. Launched EC2 instance with Ubuntu 24.04
2. Configured security groups (HTTP / custom port)
3. Installed required dependencies:
- Python
- TensorFlow
- FastAPI
- Uvicorn
4. Transferred trained model to EC2
5. Deployed model using **FastAPI**
6. Exposed API endpoint for inference

---

## FastAPI Inference Service

### API Features
- Accepts image file input
- Performs preprocessing and normalization
- Runs inference using trained U-Net model
- Returns **denoised image** as response

### Key Files
- `main.py` → FastAPI application
- `utils.py` → Custom loss functions and SSIM metric
- `denoising_model_hybrid.keras` → Trained model

---

## Technologies Used
- Python
- TensorFlow / Keras
- OpenCV
- NumPy
- Matplotlib
- FastAPI
- Uvicorn
- AWS EC2
- Ubuntu 24.04 LTS

---

## Results
- Effective removal of Gaussian and Poisson noise
- Hybrid loss preserves structural details better
- Cloud deployment enables remote inference via API

---

## Key Learnings
- Image denoising using deep learning
- U-Net architecture for image restoration
- Importance of loss function selection
- Deploying ML models on cloud infrastructure
- Hosting AI models using FastAPI on EC2

---

## Future Enhancements
- GPU-based EC2 deployment
- Real-world noisy image datasets
- Model optimization for faster inference
- Docker-based deployment

---

## Author
**Riddhi Bhagat, Krishna Joshi, Surbhi Shirvatkar**  
Course: Cloud Computing / Artificial Intelligence / Machine Learning
