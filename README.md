# Transmission Line Fault Detection Using Machine Learning

## Overview

This project develops a machine learning model for detecting faults in a transmission line using three-phase electrical measurements.

The model uses phase currents and voltages as input features and predicts whether the transmission line is operating under a normal condition or a fault condition.

## Problem Statement

Transmission line faults can cause abnormal current and voltage conditions and may lead to equipment damage and system instability.

The objective of this project is to develop a machine learning based fault detection system that can identify:

- No Fault
- Fault

from measured three-phase electrical quantities.

## Dataset

The project uses the Electrical Fault Detection and Classification dataset available on Kaggle.

Dataset:
https://www.kaggle.com/datasets/esathyaprakash/electrical-fault-detection-and-classification

The dataset contains simulated transmission-line measurements including:

- Ia - Phase A current
- Ib - Phase B current
- Ic - Phase C current
- Va - Phase A voltage
- Vb - Phase B voltage
- Vc - Phase C voltage

The original fault indicators (G, C, B, A) are used only to construct the binary target variable.

## Methodology

The project follows these steps:

1. Load and inspect the dataset
2. Create a binary fault/no-fault target
3. Select three-phase voltage and current measurements
4. Split the data into training and testing sets
5. Train a Random Forest classifier
6. Evaluate the model using accuracy, precision, recall and F1-score
7. Analyze feature importance
8. Test the model on unseen measurements
9. Save the trained model

## Machine Learning Model

### Random Forest Classifier

The main model used in this project is a Random Forest classifier with:

- 200 decision trees
- Random state = 42
- Parallel processing enabled

## Input Features

The model uses six electrical measurements:

| Feature | Description |
|---|---|
| Ia | Phase A current |
| Ib | Phase B current |
| Ic | Phase C current |
| Va | Phase A voltage |
| Vb | Phase B voltage |
| Vc | Phase C voltage |

## Target

The target variable is:

- `0` → No Fault
- `1` → Fault

## Results

Random Forest achieved:

**Test Accuracy: 96.00%**

Logistic Regression was also used as a baseline and achieved approximately:

**69.93% Test Accuracy**

The Random Forest model performed substantially better because it can capture nonlinear relationships between electrical measurements and fault conditions.

> Note: The reported performance is obtained on the provided simulated dataset and should not be interpreted as real-world field accuracy.

## Feature Importance

The Random Forest feature-importance analysis showed that phase-current measurements were the most influential features.

The approximate ranking was:

1. Ia
2. Ib
3. Ic
4. Va
5. Vc
6. Vb

## Project Structure

```text
transmission-line-fault-detection/
│
├── README.md
├── transmission_line_fault_detection.ipynb
├── transmission_line_fault_model.pkl
└── requirements.txt
