# Project_Wildlife_Classification

## Problem description
In this project, our goal is to classify the species that appear in camera trap images collected by our research partners at the Wild Chimpanzee Foundation and the Max Planck Institute for Evolutionary Anthropology. As mentioned in the about page, camera traps are one of the best tools available to study and monitor wildlife populations, and the enormous amounts of data they provide can be used to track different species for conservation efforts—once they are processed.

For our dataset, we have a trove of images from camera traps located in different sites around Taï National Park. There are seven types of critters captured in this set of images: birds, civets, duikers, hogs, leopards, other monkeys, and rodents. There are also images that contain no animals. Our job is to build a model that can help researchers predict whether an image contains one of these seven types of species.

# Conser-vision: Image Classification

This repository contains my solution to the **Conser-vision** competition hosted by [DrivenData](https://www.drivendata.org/), which focuses on using computer vision to classify wildlife species in camera trap images. The dataset is provided by the **Wild Chimpanzee Foundation** and the **Max Planck Institute for Evolutionary Anthropology**, specifically for images captured in **Taï National Park**.

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

## Dataset

The dataset consists of images taken from camera traps at different sites in **Taï National Park**. The training and testing datasets are split by site, with no overlap between the training and testing sets.

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

The model uses deep learning techniques, specifically **Convolutional Neural Networks (CNNs)**, to classify images. The model leverages **transfer learning** from a pre-trained model (e.g., ResNet50, EfficientNet) and fine-tunes it on the provided dataset to predict species classifications or blank images.

### Preprocessing
- Image augmentation techniques such as rotation, flipping, and color jittering are applied to improve model generalization.
- Images are resized to a consistent shape for input into the CNN.

## Evaluation Metric

The model's performance is evaluated using **log loss** (cross-entropy loss), which is a measure of how well the predicted probabilities match the actual labels. The lower the log loss, the better the model's performance.

## Submission Format

The final predictions are saved in a CSV file containing the predicted probabilities for each species class for the test set images. Each row contains the image `id` and the predicted probability distribution across the eight species classes (including **blank**).

```csv
id,antelope_duiker,bird,blank,civet_genet,hog,leopard,monkey_prosimian,rodent
ZJ016488,0.048233,0.189185,0.044914,0.199588,0.106118,0.132915,0.16641,0.112637
ZJ016489,0.097078,0.0614,0.026409,0.24153,0.144344,0.05178,0.287811,0.089648
...

