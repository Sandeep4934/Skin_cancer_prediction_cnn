Skin Cancer Classification using Deep Learning (HAM10000)
This project focuses on multi-class skin lesion classification using the HAM10000 dermoscopic image dataset, addressing challenges such as class imbalance and minority class detection (e.g., melanoma).

Project Overview
The goal of this project is to build a robust and clinically meaningful image classification pipeline for skin cancer detection.
Rather than optimizing only for overall accuracy, special emphasis was placed on improving recall for minority and critical classes, especially melanoma.


Baseline CNN (From Scratch)
Implemented a custom Convolutional Neural Network using Keras
Trained on augmented dermoscopic images
Served as a performance benchmark
Observation:
The baseline CNN struggled with:
Severe class imbalance
Poor recall for minority classes (melanoma, dermatofibroma, etc.)



Transfer Learning with EfficientNet:

To improve feature representation and generalization:
Used EfficientNet pretrained on ImageNet
Training was done in two phases:
Phase 1: Feature Extraction
Backbone layers frozen
Only classification head trained

Allowed the model to adapt high-level features to dermoscopic images
Phase 2: Fine-Tuning
Top layers of EfficientNet unfrozen
Trained with a very small learning rate
Enabled domain-specific feature refinement
Result:
Significant improvement in validation and test performance compared to the baseline CNN.


Despite transfer learning, minority classes were still underrepresented.
To address this:
Re-trained the model using Focal Loss
Focal Loss dynamically down-weights easy (majority-class) examples
Forces the model to focus on hard and minority-class samples
Outcome:
Substantial improvement in melanoma recall
Better macro F1-score
Reduced majority-class bias

