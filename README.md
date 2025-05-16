# Project_Wildlife_Classification

This project mainly focuses on using computer vision to classify wildlife species in camera trap images. The dataset used for this project is provided by the **Wild Chimpanzee Foundation** and the **Max Planck Institute for Evolutionary Anthropology**, specifically for images captured in **Taï National Park**.

The task is to develop a machine learning model capable of classifying images into one of the following categories:
- **antelope_duiker**
- **bird**
- **blank**
- **civet_genet**
- **hog**
- **leopard**
- **monkey_prosimian**
- **rodent**

Each image either contains one of these animal species or has no animals (blank). The goal is to build a model that predicts the probability distribution across these classes.

## Problem Overview

The competition involves classifying camera trap images, where each image is assigned a label indicating one of the species or marked as **blank** if there are no animals detected in the image. The challenge is set up as a multi-class classification problem with the added difficulty of handling images from different environmental conditions and ensuring the model generalizes well to unseen data from different sites within the park.

## Dataset Description

The dataset consists of images taken from camera traps at different sites in **Taï National Park**. There are total seven species/categories/classes of animals including rodents, birds, antelopes, civets, hogs, leapards and monkeys. Each image either contains one of these animal species or has no animals (blank). The training and testing datasets are split by site, with no overlap between the training and testing sets.

### Training Data
- **train_features**: Images of wildlife and blank scenes.
- **train_labels**: Corresponding labels for each image in `train_features`, with one-hot encoded values indicating the species class.

### Testing Data
- **test_features**: Images without labels, which are to be predicted by the model.

### Features
- **id**: Unique identifier for each image.
- **filepath**: Path to the image file.
- **site**: The site where the image was captured.

## Model

The model uses deep learning techniques, specifically **Convolutional Neural Networks (CNNs)**, to classify images. The model leverages **transfer learning** from a pre-trained model (EfficientNetB0) and fine-tunes it on the provided dataset to predict species classifications or blank images.

### Preprocessing
- Image augmentation techniques such as rotation, flipping, and color jittering are applied to improve model generalization.
- Images are resized to a consistent shape for input into the CNN.

## Evaluation Metric

The model's performance is evaluated using **log loss** (cross-entropy loss), which is a measure of how well the predicted probabilities match the actual labels. The lower the log loss, the better the model's performance.

## Results and Findings

Achieved cross entropy loss/log loss of 1.2567 on test data which is quite high from the benchmark baseline model having a log loss of 1.8210.
Since this is an advanced level practice competition on drivenata.org with over 1500 participants joined and 330 leaderboard ranks, able to achieve #24 rank i.e coming in top 7.2%

## Requirements
The following libraries and tools are required to run the code:

- **Python 3.x**
- **TensorFlow or PyTorch (for model development)**
- **Keras (for deep learning)**
- **scikit-learn (for data preprocessing and evaluation metrics)**
- **OpenCV (for image processing)**
- **Pandas (for data handling)**

### Installation
1. Clone this repository:

**git clone https://github.com/RamamAgarwal/conser-vision.git
cd conser-vision**

2. Install the required dependencies:

**pip install -r requirements.txt**



