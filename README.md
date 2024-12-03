# Defect Detection in Glass Bottles/Vials Using Custom CNN
This project aims to identify defects in pharmaceutical-grade glass bottles and vials using a custom Convolutional Neural Network (CNN). Two datasets are used to evaluate the impact of preprocessing on detection accuracy:

1.  Base images without preprocessing.
2.  Sharpened images created with edge detection.

--

## **Project Features**
Custom Dataset Class: A PyTorch dataset is implemented to load and preprocess images and labels.
Custom CNN Model: Based on ResNet-18 with modifications to classify four defect types.
Sharpened Image Dataset: Edge detection and image sharpening are applied to enhance defect features.
Model Training: Both base and sharpened datasets are used for comparison.
Metrics: Precision, recall, and F1-score are computed to evaluate model performance.

--


## **Dataset**
Structure
The dataset includes images of bottles and vials along with annotations specifying defect types:

Good
 - Broken (small)
 - Broken (large)
 - Contamination
 - Preprocessing
  
For the sharpened dataset:
 - Sobel filtering is applied to detect edges.
 - Edge information is overlaid onto the original images.

--
## **Model Architecture**
The model is based on ResNet-18 with the following modifications:
 - Input Layers: The first layers of ResNet-18 are reused.
 - Custom Fully Connected Layer: The output layer is adjusted to classify four defect types.

## Project Workflow
1. **Image Preprocessing:**
  - Resize to 224x224.
  - Apply random rotation and horizontal flip.
  - Normalize using mean and standard deviation for ImageNet.

2. **Dataset Preparation:**
  - Images are loaded using the CustomBottleDataset class.
  - Labels are mapped to integers (Good: 0, Broken (small): 1, etc.).
    
3. **Training**:
  - Optimizer: Adam.
  - Loss Function: Cross-Entropy Loss.
  - Device: CPU or GPU (Metal backend if on macOS).
  - Epochs: 10.
    
4. **Evaluation**:
  - Metrics: Precision, recall, F1-score.
  - Loss and accuracy are plotted over epochs.
    
5. **Sharpened Dataset**:
  - Edge sharpening applied using OpenCV.
  - Results compared with base images.
