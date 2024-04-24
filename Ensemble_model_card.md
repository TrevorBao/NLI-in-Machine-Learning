---
{}
---

language: en
license: cc-by-4.0
tags:

- text-classification
  repo: https://github.com/TrevorBao/NLI-in-Machine-Learning

---

# Model Card for z39535rb-z03463sy-NLI-A

<!-- Provide a quick summary of what the model is/does. -->

This is a classification model that was trained to
determine if the hypothesis is true based on the premise.

## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->

This is a classification model trained to determine the relationship between premise and hypothesis using a natural language inference approach. It employs a Stacking Classifier combining RandomForest, SVM, and Logistic Regression models, with a GradientBoostingClassifier as the final estimator to improve prediction accuracy.

- **Developed by:** Bao Renhao and Yang Shiqi
- **Language(s):** English
- **Model type:** Supervised
- **Model architecture:** Ensemble
- **Finetuned from model [optional]:** NULL

### Model Resources

<!-- Provide links where applicable. -->

- **Repository:** NULL
- **Paper or documentation:** https://link.springer.com/chapter/10.1007/3-540-45014-9_1

## Training Details

### Training Data

<!-- This is a short stub of information on the training data that was used, and documentation related to data pre-processing or additional filtering (if applicable). -->

More than 26K pairs of premise-hypothesis pairs as training data.

### Training Procedure

<!-- This relates heavily to the Technical Specifications. Content here should link to that section when it is relevant to the training procedure. -->

#### Training Hyperparameters

<!-- This is a summary of the values of hyperparameters used in training the model. -->

      - Ramdom Forest
          - n_estimators=100,
          - random_state=42
          - verbose=1
      - SVM
          - kernel='rbf'
          - probability=True
          - verbose=True
      - LogisticRegression
          - max_iter=500
          - solver='saga',
          - random_state=42
          - num_epochs: 10

#### Speeds, Sizes, Times

<!-- This section provides information about how roughly how long it takes to train the model and the size of the resulting model. -->

      - overall training time: 95min
      - duration per training epoch: No epoch used
      - model size: 172MB

## Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

### Testing Data & Metrics

#### Testing Data

<!-- This should describe any evaluation data used (e.g., the development/validation set provided). -->

A subset of the development set provided, amounting to more than 6K pairs.

#### Metrics

<!-- These are the evaluation metrics being used. -->

      - Precision 0.70
      - Recall 0.69
      - F1-score 0.69
      - Accuracy  0.69

### Results

The model obtained an F1-score of 69% and an accuracy of 69%.

## Technical Specifications

### Hardware

      - RAM: at least 16 GB
      - Storage: at least 2GB,
      - GPU: V100

### Software

      - Stence Transformers
      - Sklearn
      - joblib

## Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->

    - Using the all-MiniLM-L6-v2 Sentence-BERT model is truncates inputs longer than 512 subwords. This could potentially lead to loss of information.
    - The Stacking Classifier uses multiple models and a final estimator. This approach increases the model's complexity and computational costs.

## Additional Information

<!-- Any other information that would be useful for other people to know. -->

Embeddings from 'all-MiniLM-L6-v2' model are used to convert text data into numerical form that machine learning models can process.
Hyperparameters for base learners and the final estimator were chosen based on extensive grid search to optimize performance metrics like accuracy.
