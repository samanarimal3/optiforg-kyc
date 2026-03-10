# OptiForg — KYC Optical Forensics

OptiForg is a machine learning system designed to detect **physical presentation attacks** during KYC identity verification.  
It analyzes optical artifacts in submitted ID images to determine whether the document was captured directly or manipulated through print, screen, or lens-based attacks.

## Attack Classes

The system classifies ID submissions into four categories:

- Genuine — Direct camera capture of a real ID card
- Print Attack — Photo of a printed copy of an ID
- Screen Attack — Photo of an ID displayed on a phone or monitor
- Lens Attack — Optical lens manipulation causing geometric distortion

## Approach

The pipeline analyzes both image content and optical artifacts:

1. Extract forensic features from the input image
2. Generate a multi-channel feature representation combining RGB data with optical forensic signals
3. Classify the image using a modified EfficientNet-B0 deep learning model
4. Produce an attack prediction with a confidence score

The system examines signals such as:

- Blur patterns
- Frequency artifacts and Moiré patterns
- Geometric consistency and distortion

Synthetic training data is generated to simulate common real-world artifacts including print grain, display pixel grids, and lens distortion.

## Model

- Backbone: EfficientNet-B0 (pretrained on ImageNet)
- Input: Multi-channel image combining RGB and forensic features
- Output: 4-class attack prediction

## Project Structure
optiforg/
├── data/
│ ├── genuine/
│ ├── print_attack/
│ ├── screen_attack/
│ └── lens_attack/
├── checkpoints/
│ └── best_model.pt
├── results/
└── OptiForg_KYC_Optical_Forensics.ipynb


## Requirements
torch
torchvision
opencv-python
numpy
scipy
Pillow
scikit-learn
matplotlib
pandas

## Motivation

Identity fraud during KYC onboarding often uses presentation attacks such as printed IDs or screen recaptures.  
OptiForg focuses on detecting these attacks by analyzing optical forensic signatures in the submitted image before document verification is performed.
