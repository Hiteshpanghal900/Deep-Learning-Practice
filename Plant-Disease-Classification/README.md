# Plant Disease Classification
This project fine-tunes a **ResNet-50 convolutional neural network** on the cleaned and pre-split **PlantVillage dataset** from the `dlp-ga-9-image-classification` Kaggle competition. The goal is to classify plant leaf images into 38 healthy/diseased classes and generate a submission-ready CSV for evaluation.

## Dataset Overview
* **Train:** 43,441 images
* **Test:** 10,861 images
* **Classes:** 38
* **Format:** .jpg

## Directory Structure of Data
```
train/
   ├── Apple_Apple_scab/
   ├── Corn_maize_healthy/
   └── ... (38 class folders)
test/
   ├── image_00001.jpg
   ├── image_00002.jpg
   └── ...
```

## Download Dataset (Kaggle CLI)
Ensure Kaggle CLI is installed and authenticated, then run:
```
kaggle competitions download -c dlp-ga-9-image-classification
```

## Approach
* Used transfer learning with a pretrained ResNet-50 model.
* Replaced the final classification layer with a 38-class output head.
* Applied image preprocessing and augmentation (resize, normalization, flips, etc.).
* Trained the model using fine-tuning to adapt ResNet-50 to plant disease features.
* Generated predictions for all test images.
* Created a submission.csv containing:
  * Image_ID → filename without “.jpg”
  * Label → predicted class ID (0–37)

## Submission Format Example
```
Image_ID,Label
image_00001,12
image_00002,5
image_00003,27
```

