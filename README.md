Breast Cancer Segmentation Using UNET and Attention UNET Models

Project Overview:
This project focuses on developing and implementing deep learning models for the segmentation of breast cancer in ultrasound images. The primary objective is to segment breast tumors (both benign and malignant) to aid in early diagnosis. Two models are employed: the UNET and Attention UNET architectures. The dataset used for this research comes from the Breast Ultrasound Images dataset (Kaggle, 2020). The segmentation models aim to distinguish between benign and malignant tumors in ultrasound images to improve diagnosis accuracy.

2. Architecture and Models
2.1. UNET Model
The UNET architecture is a popular model for biomedical image segmentation, known for its encoder-decoder structure. This architecture preserves spatial information while downsampling and upsampling, making it effective for image segmentation tasks.

Encoder: Reduces the spatial dimensions while increasing the depth of feature maps to capture high-level details.
Decoder: Mirrors the encoder and uses transposed convolutions to upsample and reconstruct the segmented image.
Final Output: Produces a binary mask that segments tumor regions from ultrasound images.

2.2. Attention UNET Model
The Attention UNET enhances the original UNET by incorporating attention mechanisms. These mechanisms help the model focus on relevant areas of the image, improving segmentation accuracy, especially in detecting subtle and small tumors.

Attention Mechanism: Applied within skip connections, allowing the model to prioritize important regions in the feature maps.
Enhanced Skip Connections: Attention gates are introduced before concatenating encoder and decoder features, resulting in more accurate segmentation.

2.3. Grad-CAM for Explainability
To improve model transparency, Grad-CAM (Gradient-weighted Class Activation Mapping) is used. Grad-CAM produces visual heatmaps showing which areas of the input image influence the model’s predictions, making the decision-making process interpretable to clinicians.

3. Dataset
The dataset comprises 780 ultrasound images of breast tissue, divided into three categories: normal, benign, and malignant.

Source: Breast Ultrasound Images Dataset (Kaggle, 2020).
Image Details: Each image has a resolution of approximately 500x500 pixels, and ground truth masks for benign and malignant tumors are provided.
Dataset Split:
Training Set: 70%
Validation Set: 20%
Test Set: 10%
4. Data Preprocessing
4.1. Mask Loading and Combination
The dataset includes separate masks for benign and malignant tumors. These masks are combined into a single comprehensive mask for each image to represent the areas containing tumors.

4.2. Data Augmentation
Several augmentation techniques are applied to increase the diversity of the dataset:

Resizing: All images are resized to 256x256 pixels.
Rotation: Random rotations (up to 45 degrees) are applied.
Flipping: Horizontal and vertical flips are used to enhance variability.
Zooming: Random zooms are applied with a zoom range of 0.2.
Shearing: Images are sheared with a shear range of 0.2.
5. Model Training and Optimization
Loss Functions: A combination of Binary Cross-Entropy and Dice Loss is used to handle class imbalance and improve segmentation on tumor pixels.
Optimizer: Adam Optimizer is used for its adaptive learning rate.
Training Setup: Early stopping is implemented to prevent overfitting. The models are trained for 60 epochs with a batch size of 6.
Hardware: The training is conducted on a Tesla T4 GPU, providing necessary computational power.
6. Evaluation Metrics
The models are evaluated using the following metrics:

Dice Coefficient: Measures the overlap between the predicted and ground-truth segmentation masks.
Intersection Over Union (IOU): Another metric to assess segmentation accuracy by calculating the overlap of prediction and actual mask.
7. Model Explainability
Grad-CAM is employed to visually interpret the areas of the image that influence the model’s predictions. This helps clinicians understand and validate the model’s decision-making process, especially in sensitive medical applications.

8. Challenges and Solutions
8.1. TensorFlow Compatibility Issues
The project encountered issues due to TensorFlow (v2.16.1) updates. This was resolved by adjusting the codebase to ensure compatibility.
8.2. Image and Mask Misalignment
Misaligned image-mask pairs were addressed using the natsort Python library to ensure proper alignment.
8.3. Slow CPU Training
Initially, model training on a CPU was slow. Switching to Google Colab with a GPU resolved this issue, significantly speeding up training times.
9. Requirements
9.1. Hardware
Tesla T4 GPU (15 GB memory) for efficient training.
9.2. Software
TensorFlow/Keras for model development.
Python Libraries:
Numpy, OpenCV, Sklearn, Seaborn, Matplotlib for data handling and visualization.
10. Getting Started
10.1. Installation
To run the project, clone the repository and install the necessary dependencies:
git clone <repo-url>
cd project-folder
pip install -r requirements.txt

10.2. Running the Model
Preprocess the dataset using the scripts provided.
Train the model by running:
python train.py
To evaluate the model, use the command:
python evaluate.py
10.3. Applying Grad-CAM
To generate Grad-CAM heatmaps, run:
python grad_cam.py

