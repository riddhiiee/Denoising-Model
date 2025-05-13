# IDSA Image Denoising Model

The project uses the BSDS500 (Berkeley Segmentation Dataset), a curated dataset of natural images that contains 500 natural images divided into training, validation, and test sets. It contains high-quality images to which synthetic noise (Gaussian,Poisson noise) are added for training, testing and evaluation purposes.
This project implements a deep learning model for image denoising using a U-Net architecture. 
This project implements an image denoising model using deep learning. The model is trained to remove noise from images using different loss functions:

- **SSIM (Structural Similarity Index)**
- **MSE (Mean Squared Error)**
- **HYBRID Loss (SSIM + MAE)**

The model follows an encoder-decoder architecture (similar to U-Net) designed for image-to-image translation tasks. It takes a noisy input image and outputs a denoised version.
 ****
- 
