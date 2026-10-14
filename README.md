# 🌿 AgriSense — Plant Disease Detection

**An AI-powered plant disease detection initiative for Tomato, Marigold, and Mint.**

AgriSense aims to help identify potential plant diseases using plant images and disease-related datasets. By organizing crop-specific data and preparing it for machine learning, the project establishes a foundation for developing an image-based disease classification system.

The long-term goal is to complement crop growth monitoring with disease detection, helping identify potential crop health problems earlier and supporting informed agricultural decisions.

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Crops Covered](#-crops-covered)
- [Repository Contents](#-repository-contents)
- [Understanding the Datasets](#-understanding-the-datasets)
- [Proposed Disease Detection Workflow](#-proposed-disease-detection-workflow)
- [Dataset Preparation](#-dataset-preparation)
- [Machine Learning Approach](#-machine-learning-approach)
- [Technology Stack](#-technology-stack)
- [Future Implementation](#-future-implementation)
- [Limitations](#-limitations)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)

## 🌱 Project Overview

Plant diseases can affect crop health, growth, and productivity. Early identification of visible symptoms can help farmers investigate potential problems and take appropriate action.

AgriSense aims to develop a disease detection system that uses plant images and machine learning to classify visible disease symptoms.

The project focuses on three crops:

- 🍅 **Tomato:** Disease-related image data for investigating common tomato plant diseases.
- 🌼 **Marigold:** Crop-specific disease data for studying disease symptoms affecting marigold plants.
- 🌿 **Mint:** Disease-related data for exploring disease classification in mint plants.

The current repository organizes disease dataset resources for these crops. The actual diseases, image counts, labels, and sources must be verified from the individual workbooks and image archive before model training.

## 🎯 Objectives

1. Collect and organize disease-related datasets for tomato, marigold, and mint.
2. Identify the available disease categories and corresponding image resources.
3. Verify dataset sources, licenses, labels, and image quality.
4. Prepare image data for machine learning.
5. Develop an image classification model to identify supported disease categories.
6. Evaluate the model using appropriate validation and testing procedures.
7. Explore confidence-based predictions and understandable disease information.
8. Integrate disease detection with the AgriSense crop growth monitoring system in a future phase.

## 🌾 Crops Covered

| Crop | Dataset focus | Intended application |
|---|---|---|
| 🍅 Tomato | Tomato disease datasets | Classification of supported tomato disease categories |
| 🌼 Marigold | Marigold disease datasets | Identification of supported marigold disease categories |
| 🌿 Mint | Mint disease datasets and image archive | Classification of supported mint disease categories |

The availability and quality of disease labels may differ between crops. Each crop should be evaluated separately before combining the datasets into a single model.

## 📂 Repository Contents

The repository currently contains the following files.

| File | Purpose |
|---|---|
| [AgriSense Marigold Disease Datasets](AgriSense_Marigold_Disease_Datasets.xlsx) | Workbook containing marigold disease dataset information |
| [Mint Disease Datasets — Real Data](Mint_Disease_Datasets_Real_Data%20%281%29.xlsx) | Workbook organized around mint disease data |
| [Tomato Disease Datasets](Tomato_Disease_Datasets%20%281%29%20%281%29.xlsx) | Workbook containing tomato disease dataset information |
| [Mint Disease Dataset ZIP](mint_disease_dataset.zip) | Archive containing mint disease dataset resources |

These links refer to files stored in this GitHub repository.

**Important:** An Excel workbook documenting datasets is not necessarily the same as a folder containing the original plant images. Check the contents of each workbook and the ZIP archive to determine which data is directly available for training.

## 📊 Understanding the Datasets

The datasets form the foundation for developing and evaluating the disease detection model.

### 1. Tomato disease dataset

The tomato workbook can be used to review available tomato disease datasets, their sources, supported disease categories, and access links.

Before training, verify whether the actual images are stored locally, linked externally, or referenced only in the workbook.

### 2. Marigold disease dataset

The marigold workbook organizes disease-related data for the project's marigold use case.

Verify the source, image availability, disease labels, and number of examples for each category. Do not assume that tomato disease labels or reference images can be used as substitutes for marigold-specific evidence.

### 3. Mint disease dataset

The mint workbook and ZIP archive provide resources for the mint disease detection component.

Inspect the archive to determine its folder structure, image formats, class labels, and number of images. Check whether the images represent actual field conditions and whether their labels have been independently verified.

### Dataset verification checklist

Before using any dataset for model development, verify:

- Original dataset name and source URL.
- Dataset license and attribution requirements.
- Crop species and disease categories represented.
- Total number of images and images per class.
- Whether images are real, synthetic, augmented, or mixed.
- Image format, resolution, and quality.
- Whether labels have been verified by a reliable source.
- Whether healthy plant images are included.
- Whether the data includes field images or only controlled-background images.
- Whether duplicates or near-duplicate images exist.
- Whether the dataset is suitable for training, validation, and testing.

## 🔄 Proposed Disease Detection Workflow

The intended workflow is:

1. **Dataset collection:** Gather suitable disease-related plant images from verified sources.
2. **Dataset inspection:** Review labels, image quality, source information, and class distribution.
3. **Image preprocessing:** Resize images, normalize pixel values, and prepare them for the chosen model.
4. **Dataset splitting:** Create training, validation, and testing sets while preventing duplicate-image leakage.
5. **Model training:** Train an image classification model using the available labeled images.
6. **Disease prediction:** Process a new plant image and predict a supported class.
7. **Confidence assessment:** Report prediction confidence and flag uncertain predictions for further inspection.
8. **Result presentation:** Display the predicted class and relevant, verified information about the condition.
9. **Future integration:** Connect the disease detection component to the broader AgriSense platform.

This workflow describes the planned approach; it does not imply that a trained model or operational application is already present in this dataset repository.

## 🧹 Dataset Preparation

Proper preparation is essential for dependable disease classification.

### Image organization

A possible directory structure for the prepared images is:

```text
dataset/
├── tomato/
│   ├── healthy/
│   ├── disease_class_1/
│   └── disease_class_2/
│
├── marigold/
│   ├── healthy/
│   ├── disease_class_1/
│   └── disease_class_2/
│
└── mint/
    ├── healthy/
    ├── disease_class_1/
    └── disease_class_2/
```

Replace the placeholder class names with verified disease labels. Create only the folders corresponding to classes that are actually supported by the collected data.

### Preprocessing steps

- Remove corrupted and unreadable images.
- Identify duplicate images.
- Standardize image dimensions.
- Normalize image values according to the model requirements.
- Check for class imbalance.
- Apply suitable image augmentation only to training data.
- Preserve a separate validation and test set.
- Keep source and label information for traceability.

## 🤖 Machine Learning Approach

Several approaches may be considered depending on dataset size, image quality, and available computing resources.

### Convolutional Neural Networks (CNNs)

CNNs can learn visual features from plant images and classify images into supported disease categories.

### Transfer learning

Pretrained architectures such as MobileNetV2 or EfficientNet can be fine-tuned for the target crop and disease classes. Transfer learning is a candidate approach, not a claim that a specific model has already been trained.

### Model evaluation

Evaluate the model using:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Confusion matrix.
- Per-class performance.

For agricultural applications, per-class recall and precision are particularly important because a model can achieve high overall accuracy while performing poorly on a less-represented disease.

If multiple images come from the same plant, image session, or original source, keep related samples in the same data split where possible. This helps avoid overly optimistic evaluation results.

## 🛠️ Technology Stack

The following tools are potential choices for implementation.

| Component | Candidate technology |
|---|---|
| Dataset processing | Python, Pandas, NumPy |
| Image processing | Pillow, OpenCV |
| Deep learning | TensorFlow/Keras or PyTorch |
| Transfer learning | MobileNetV2 or EfficientNet |
| Evaluation | Scikit-learn |
| Visualization | Matplotlib |
| Model deployment | FastAPI or Flask |
| Future user interface | Web or mobile application |

The final technology stack should be selected according to the team's implementation requirements and available hardware.

## 🚀 Future Implementation

- [ ] Verify all disease dataset sources and licenses.
- [ ] Inspect the three Excel workbooks and mint ZIP archive.
- [ ] Document the actual disease classes for each crop.
- [ ] Collect or download the original image datasets.
- [ ] Verify labels and remove duplicate or unusable images.
- [ ] Prepare balanced training, validation, and testing datasets where feasible.
- [ ] Train an initial baseline image classification model.
- [ ] Evaluate model performance for each crop and disease category.
- [ ] Test the model on independent images collected under practical conditions.
- [ ] Develop an image upload and prediction interface.
- [ ] Display confidence scores and uncertainty warnings.
- [ ] Add carefully verified disease information and management guidance.
- [ ] Integrate disease detection with crop growth monitoring in AgriSense.

## ⚠️ Limitations

- A dataset reference does not guarantee that the original images are included in this repository.
- Disease categories and image counts must be verified before training.
- Images captured in controlled conditions may not represent real agricultural environments.
- Visually similar diseases and environmental stress symptoms can lead to incorrect predictions.
- A model cannot reliably identify diseases that are absent from its training classes.
- Prediction confidence does not guarantee that a diagnosis is correct.
- Disease detection from images is different from crop growth monitoring and environmental anomaly detection.
- Treatment recommendations require reliable, crop-specific information and should not be generated solely from an unverified model prediction.

The system should present its output as an AI-assisted assessment rather than a guaranteed diagnosis.

## 📁 Project Structure

The repository currently contains these dataset resources:

```text
AgriSense--Disease-Detection/
│
├── AgriSense_Marigold_Disease_Datasets.xlsx
├── Mint_Disease_Datasets_Real_Data (1).xlsx
├── Tomato_Disease_Datasets (1) (1).xlsx
└── mint_disease_dataset.zip
```

As development progresses, additional directories may be introduced for image preprocessing, training scripts, evaluation reports, trained model files, and application integration.

## 🤝 Contributing

Contributions are welcome as the project develops.

1. Document the original source of every dataset.
2. Preserve dataset licenses and attribution requirements.
3. Keep crop and disease labels accurate and consistent.
4. Clearly distinguish real images from synthetic or augmented images.
5. Document preprocessing and model evaluation methods.
6. Avoid unsupported accuracy or diagnostic claims.
7. Contribute improvements through GitHub branches and pull requests.

## 📄 License and Attribution

Verify the licensing terms of every external dataset before copying, redistributing, or using it in a public application. The repository's availability does not automatically grant permission to redistribute third-party datasets.

## 🌱 Project Vision

AgriSense aims to combine disease detection with crop growth monitoring to provide a more comprehensive view of plant health.

By developing crop-specific datasets and validating machine learning models, the project seeks to build a foundation for earlier disease identification and better-informed agricultural decisions.

**Smarter detection. Healthier crops. Better-informed farming.**
