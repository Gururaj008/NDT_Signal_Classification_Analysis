# Signal Flaw Detection with Hybrid Deep Learning & Feature Engineering

> **Objective:** Build an end-to-end, reproducible pipeline to automatically detect potential flaws in Non-Destructive Testing (NDT) signals by combining classical feature engineering with a lightweight 1D CNN.

## Table of Contents

* [1. Why This Matters (Need / Motivation)](#1-why-this-matters-need--motivation)
* [2. Input Data](#2-input-data)
* [3. Pre-Processing](#3-pre-processing)
* [4. Models Used](#4-models-used)
* [5. Results](#5-results)
* [6. Implications](#6-implications)
* [7. Repository Structure](#7-repository-structure)
* [8. How to Run](#8-how-to-run)
* [9. Future Work](#9-future-work)
* [10. License](#10-license)

---

## 1. Why This Matters (Need / Motivation)

Manual inspection of NDT waveform data is time-consuming, subjective, and does not scale. An automated approach reduces human error, speeds up the inspection process, and ensures consistent flaw detection.

---

## 2. Input Data

* **Dataset:** NDT signal recordings (time-series data).
* **Labels:** Binary classification – *Flaw* vs *No Flaw*.
* **Format:** CSV files containing raw signal amplitudes.

---

## 3. Pre-Processing

* **Noise Reduction:** Applied smoothing filters to remove high-frequency noise.
* **Segmentation:** Signals were segmented into uniform windows.
* **Feature Extraction:** Computed statistical and frequency-domain features (RMS, skewness, FFT peaks).
* **Normalization:** Applied Min-Max scaling for feature consistency.
* **Data Augmentation:** Introduced synthetic variations to handle class imbalance.

---

## 4. Models Used

1. **1D Convolutional Neural Network (1D-CNN):** For automated feature learning from raw signals.
2. **Random Forest Classifier:** Trained on engineered features.
3. **Hybrid Model:** Combined CNN feature embeddings with classical features to enhance accuracy.

---

## 5. Results

* **Accuracy:** 0.998 on the test set.
* **Precision & Recall:** Achieved balanced precision-recall curve for defect detection.

---

## 6. Implications

* Demonstrates that combining deep learning with domain-specific feature engineering yields superior performance in flaw detection.
* Can be extended to other NDT modalities and industrial signal monitoring applications.
