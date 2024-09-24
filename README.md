Overview
This project uses UNET and Attention UNET models for breast cancer tumor segmentation in ultrasound images.

Creating New Colab Notebook
Open your Google Drive
Create a new notebook via Right click > More > Colaboratory

Requirements
Hardware
Tesla T4 GPU (or similar)
Software
TensorFlow/Keras
Python 3.x
Required libraries: Numpy, OpenCV, Sklearn, Seaborn, Matplotlib

install necessaries libraries

!pip install natsort
!pip install livelossplot
!pip install lime

Dataset
Dataset: Breast Ultrasound Images (Kaggle, 2020)
Download and place the dataset in the data/ directory. 


Steps to Run the Project in Google Colab
Set Up Google Drive
First, you'll need to mount your Google Drive to access the dataset:

2. Upload the Dataset
Make sure your dataset is in your Google Drive.

Mount your Google Drive
# Import the drive module from google.colab
from google.colab import drive
import zipfile
import os
# Mount Google Drive to the specified directory '/content/drive'
drive.mount('/content/drive')

# incase you are not storing the file in google drive, set the FILE directory automatically.
# FILE_DIR = '';

Notes
Ensure that the dataset is properly uploaded
You can access your results and saved models directly from Google Drive.

