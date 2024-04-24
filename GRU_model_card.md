---
{}
---

language: en
license: cc-by-4.0
tags:

- text-classification
  repo: https://github.com/TrevorBao/NLI-in-Machine-Learning

---

# Model Card for z39535rb-z03463sy-NLI-B

<!-- Provide a quick summary of what the model is/does. -->

This is a classification model that was trained to
determine if the hypothesis is true based on the premise.

## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->

This is a natural language inference model trained to predict the relationship between premise and hypothesis. It employs a neural network architecture with bidirectional GRU layers and an attention mechanism.

- **Developed by:** Bao Renhao and Yang Shiqi
- **Language(s):** English
- **Model type:** Bidirectional Gated Recurrent Unit with Attention Mechanism
- **Model architecture:** BiGRUAttentionModel
- **Finetuned from model [optional]:** NULL

### Model Resources

<!-- Provide links where applicable. -->

- **Repository:** NULL
- **Paper or documentation:** https://ieeexplore.ieee.org/abstract/document/8053243

## Training Details

### Training Data

<!-- This is a short stub of information on the training data that was used, and documentation related to data pre-processing or additional filtering (if applicable). -->

More than 26K pairs of premise-hypothesis pairs as training data.

### Training Procedure

<!-- This relates heavily to the Technical Specifications. Content here should link to that section when it is relevant to the training procedure. -->

#### Training Hyperparameters

<!-- This is a summary of the values of hyperparameters used in training the model. -->

      - GRU Layer:
        - Number of hidden units: 64
        - Bidirectionality: True
    - Dropout rate: 0.4
    - Fully Connected Layers:
        - Dimensions in the first linear layer: Maps 128 to 64
        - Dimensions in the second linear layer: Maps 64 to 1
    - Learning rate: 0.0005
    - epochs: 15

#### Speeds, Sizes, Times

<!-- This section provides information about how roughly how long it takes to train the model and the size of the resulting model. -->

      - overall training time: 1min
      - duration per training epoch: 2s
      - model size: 1291KB

## Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

### Testing Data & Metrics

#### Testing Data

<!-- This should describe any evaluation data used (e.g., the development/validation set provided). -->

A subset of the development set provided, amounting to more than 6K pairs.

#### Metrics

<!-- These are the evaluation metrics being used. -->

      - Precision 0.71
      - Recall 0.71
      - F1-score 0.71
      - Accuracy  0.71

### Results

The model obtained an F1-score of 71% and an accuracy of 71%.

## Technical Specifications

### Hardware

      - RAM: at least 16 GB
      - Storage: at least 2GB,
      - GPU: V100

### Software

      - Stence Transformers
      - PyTorch
      - sklearn

## Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->

    - Using the all-MiniLM-L6-v2 Sentence-BERT model is truncates inputs longer than 512 subwords. This could potentially lead to loss of information.
    - The Stacking Classifier uses multiple models and a final estimator. This approach increases the model's complexity and computational costs.

## Additional Information

<!-- Any other information that would be useful for other people to know. -->

The Sentence-BERT model all-MiniLM-L6-v2 truncates inputs longer than 512 subwords
Bidirectional GRU and attention mechanisms increases computational complexity.
