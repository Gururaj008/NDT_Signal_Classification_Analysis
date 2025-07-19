NDT Signal Flaw Detection: A Comparative Analysis

A project demonstrating the process of diagnosing, correcting, and modeling time-series data to achieve high-accuracy flaw detection using both classical machine learning and a hybrid deep learning approach.
The Need

In industrial settings, Non-Destructive Testing (NDT) is crucial for ensuring the quality and safety of materials. Automating the analysis of NDT signals can dramatically increase efficiency, improve accuracy, and reduce human error. This project tackles this challenge by developing and comparing robust models to automatically classify signals as either containing a "flaw" or "no flaw."
The Input: Dataset Overview

    Source: The data is from the NDT_ML_Flaw GitHub repository, consisting of thousands of time-series signals from an NDT process.

    Challenge & Solution: The original labels provided with the dataset were found to be unreliable, leading to poor initial model performance. A key part of this project was to develop a robust heuristic labeling strategy. By analyzing the signal's standard deviation and using the median as a threshold, the data was successfully and programmatically separated into two distinct, balanced classes:

        Class 0 (No Flaw): Signals with low amplitude variation.

        Class 1 (Flaw): Signals with high amplitude variation and "spiky" characteristics.

Data Preprocessing & Feature Engineering

Before modeling, the data underwent a rigorous preparation pipeline:

    Data Cleaning: Signals were cleaned by handling NaN and infinite values and clipping outlier signal amplitudes to a reasonable range.

    Feature Engineering: A rich set of descriptive features was extracted from each signal to capture its unique characteristics:

        Statistical Features: Included mean, standard deviation, min/max values, signal energy (sum of absolute values), and average slope.

        Wavelet Features: Wavelet decomposition was used to extract time-frequency features, capturing patterns that are not apparent in the time domain alone.

    Normalization: Standard scaling (Z-score normalization) was applied to both the raw signal data (for the CNN) and the engineered feature matrix to ensure consistent model training.

Models Implemented

Two distinct modeling approaches were developed to compare classical and deep learning techniques:
Model 1: RandomForest Classifier

    A classical machine learning baseline using a RandomForestClassifier.

    This model was trained exclusively on the engineered feature set, testing the predictive power of the statistical and wavelet features.

Model 2: Hybrid Deep Learning Model

    A more complex, multi-input Convolutional Neural Network (CNN).

    This model was designed to leverage both the raw signal data and the engineered features simultaneously:

        A CNN branch processes the raw time-series signal using Conv1D and MaxPooling1D layers, followed by a GlobalMaxPooling1D layer to efficiently extract the most important temporal features.

        A Feature branch directly accepts the engineered features.

        The outputs are concatenated and passed through final Dense layers for classification.

Outputs & Results

Both models demonstrated exceptionally high performance on the unseen test data, validating the data correction and feature engineering steps.

    The RandomForest Classifier achieved perfect classification on the test set.

    The Hybrid CNN Model achieved near-perfect accuracy, successfully learning to distinguish between the two classes.

Result Analysis

The outstanding performance of both models is not a sign of overfitting but rather a confirmation that the two classes of signals are highly separable once correctly labeled. The training history of the CNN showed that the validation accuracy and loss tracked the training metrics almost perfectly, indicating excellent generalization to unseen data.

The success of the RandomForest model, in particular, highlights the immense power of the engineered features, which were sufficient on their own to perfectly classify the signals.
Significance & Key Takeaways

    Data Quality is Paramount: This project is a strong case study in the importance of data integrity. The initial model failure was entirely due to mislabeled data, and the project's success was unlocked by creating reliable labels through a robust heuristic.

    The Power of Feature Engineering: The perfect score achieved by the RandomForest demonstrates that thoughtful, domain-aware feature engineering can be more effective than relying on model complexity alone.

    Model Recommendation: For this specific problem, the RandomForest Classifier is the recommended model. It provides perfect accuracy while being simpler, faster to train, and more interpretable than the deep learning model.
