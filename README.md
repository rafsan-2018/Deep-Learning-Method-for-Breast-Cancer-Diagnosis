Breast Cancer Segmentation Using UNET and Attention UNET

Project Overview
This project develops deep learning models for segmenting breast cancer in ultrasound images using UNET and Attention UNET architectures. The goal is to identify benign and malignant tumors to improve early diagnosis. The dataset used is the Breast Ultrasound Images dataset from Kaggle (2020).

Model Architecture
1. UNET Model
UNET is a CNN-based model for image segmentation, using an encoder-decoder structure to capture both spatial and semantic information, producing binary masks that segment tumor regions.

2. Attention UNET Model
This model enhances UNET with attention mechanisms, helping focus on key image regions. This improves segmentation accuracy, especially for small or hard-to-detect tumors.

3. Grad-CAM for Explainability
Grad-CAM generates visual heatmaps to highlight areas that influenced the model’s predictions, improving transparency and aiding clinical interpretation.

Dataset
Source: Breast Ultrasound Images (Kaggle, 2020).
Images: 780 PNG images, categorized as normal, benign, and malignant.
Split: 70% training, 20% validation, 10% test.
Data Preprocessing
Mask Combination: Benign and malignant tumor masks are merged for each image.
Data Augmentation:
Resizing: 256x256 pixels
Rotation, flipping, zooming, and shearing to increase variability.
Model Training
Loss Functions: Binary Cross-Entropy and Dice Loss.
Optimizer: Adam.
Training: 60 epochs, batch size of 6.
Hardware: Tesla T4 GPU.
Evaluation Metrics

Dice Coefficient: Measures overlap between predicted and ground-truth masks.

Intersection Over Union (IOU): Evaluates segmentation accuracy.
Challenges

TensorFlow Issues: Addressed by code adjustments for compatibility.

Image-Mask Misalignment: Solved using the natsort Python library.

Slow CPU Training: Resolved by using GPU resources in Google Colab.

Requirements
Hardware: Tesla T4 GPU.
Software: TensorFlow/Keras, Python libraries (Numpy, OpenCV, etc.).
Getting Started
Clone the repository and install dependencies:
Copy code
git clone <repo-url>
cd project-folder
pip install -r requirements.txt
Train the model:
Copy code
python train.py
Evaluate the model:
Copy code
python evaluate.py
Generate Grad-CAM heatmaps:
Copy code
python grad_cam.py
