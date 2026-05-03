# Pneumonia Detection from Paediatric Chest X-rays

## WM9B7 AIDL — Individual Assessment

**Name:** Palinda Attanayake (u5744388)
**Dataset:** PneumoniaMNIST, MedMNIST v2  (https://medmnist.com/)

## Notebook files

This submission contains two notebook versions using different image resolutions:

- `pneumonia_classification.ipynb` — uses **128 × 128** image resolution
- `pneumonia_classification_28.ipynb` — uses **28 × 28** image resolution

The 128 × 128 version is used for the main experimental analysis, while the 28 × 28 version is included for comparison with the original lightweight PneumoniaMNIST setting.

## Environment

The notebooks were developed and tested in **Azure ML** using the kernel:

`Python 3.10 - AzureML`

The code supports GPU execution when CUDA is available, but also runs on CPU as a fallback.

## How to run

Open the required notebook and click:

**Run All**

The notebooks are self-contained. The PneumoniaMNIST dataset is downloaded automatically by the `medmnist` library on the first run, so no local dataset files are required.
Currently all the epochs set to 1 in the first code cell, Please change them to following values get the given results,
MLP_EPOCH = 15
CNN_EPOCH = 25
RESNET_EPOCH= 10. Cross validation also commented in this. 

## Expected runtime

Approximate runtime on an Azure ML CUDA GPU:

- Full training epochs: around **4 minutes**
- `MLP_EPOCHS = 1`, `CNN_EPOCHS = 1`, keeping `RESNET_EPOCHS` unchanged: around **1.5 minutes**
- All model epochs set to `1`: around **30 seconds**

Runtime may vary depending on hardware availability and Azure ML resource allocation.

## Reproducibility

All random seeds are fixed using:

`SEED = 42`

Small differences in results may still occur across hardware because some CUDA convolution operations are not fully deterministic.

## What the notebooks include

The notebooks cover:

1. Environment setup, imports, random seeds, and device selection
2. Dataset download and exploration
3. Preprocessing, normalisation, DataLoaders, and weighted sampling
4. Logistic Regression baseline using flattened pixels
5. MLP model
6. CNN model
7. ResNet18 transfer learning model
8. Evaluation using recall, specificity, F1-score, AUC, confusion matrices, ROC curves, and Grad-CAM

## Primary evaluation metric

The primary metric is **recall for the Pneumonia class**.

This is because, in a screening or triage setting, missing a pneumonia case is more clinically serious than sending a normal case for additional review. Recall is therefore reported alongside AUC, specificity, F1-score, and confusion matrices to provide a more complete evaluation.

## Dataset citation

Jiancheng Yang, Rui Shi, Donglai Wei, Zequan Liu, Lin Zhao, Bilian Ke, Hanspeter Pfister, Bingbing Ni.  
“MedMNIST v2: A large-scale lightweight benchmark for 2D and 3D biomedical image classification.”  
*Scientific Data*, 2023.

Jiancheng Yang, Rui Shi, Bingbing Ni.  
“MedMNIST Classification Decathlon: A Lightweight AutoML Benchmark for Medical Image Analysis.”  
*IEEE 18th International Symposium on Biomedical Imaging (ISBI)*, 2021.

## Licence

The MedMNIST PneumoniaMNIST dataset is licensed under the **Creative Commons Attribution 4.0 International Licence (CC BY 4.0)**.