---
license: mit
language:
- en
datasets:
- iris
metrics:
- accuracy
- f1
pipeline_tag: tabular-classification
---

## Model Details
- **Model name:** Iris Random Forest Classifier
- **Author:** NtechOFAST
- **Date:** 9 October 2026
- **Version:** 1.0
- **Model type:** RandomForestClassifier (scikit-learn)
- **License:** MIT

## Intended Use
This model is intended to classify Iris flowers into one of three species:
Iris setosa, Iris versicolor, or Iris virginica, based on sepal and petal
measurements.

**Intended users:** Students, researchers, and developers for educational
and demonstration purposes.

**Intended use cases:** Machine learning education, experimentation, and
demonstration of multi-class classification.

**Out-of-scope uses:** This model should not be used for high-stakes
decision-making or in production environments without additional validation.

## Factors (Facteurs)
The model's performance may be influenced by the distribution of the input
features, including sepal length, sepal width, petal length, and petal width.

Class balance may also affect performance. The Iris dataset is relatively
balanced across the three target classes.

Performance on samples whose measurements differ significantly from those
represented in the training dataset may be lower.

## Metrics (Métriques)
The model is evaluated using accuracy, precision, recall, and F1-score.

These metrics are appropriate for a multi-class classification problem:
- **Accuracy** measures the overall proportion of correct predictions.
- **Precision** measures how many predictions for a class are correct.
- **Recall** measures how many samples of a class are correctly identified.
- **F1-score** provides a balance between precision and recall.

On the test set, the model achieved an accuracy of **1.0000 (100%)**.
Precision, recall, and F1-score were also **1.00 for all three classes**.

## Training Data (Données d'entraînement)
The model was trained using the Iris flower dataset.

- **Dataset:** Iris flower dataset
- **Source:** `sklearn.datasets.load_iris`
- **Training set size:** 120 samples
- **Features:**
  - Sepal length
  - Sepal width
  - Petal length
  - Petal width
- **Target:** Iris species
  - Setosa
  - Versicolor
  - Virginica

The dataset contains numerical measurements of Iris flowers used to predict
one of the three Iris species.

## Evaluation Data (Données d'évaluation)
The model was evaluated on a test subset of the Iris flower dataset.

- **Dataset:** Iris flower dataset
- **Source:** `sklearn.datasets.load_iris`
- **Test set size:** 30 samples
- **Purpose:** Evaluate the model on data not used during training
- **Target classes:** Setosa, Versicolor, and Virginica

The test set is separate from the training set and is used to evaluate
the model's ability to generalize to unseen samples.

## Quantitative Analyses (Analyses quantitatives)
The model achieved consistent performance across all three Iris classes.

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Setosa | 1.00 | 1.00 | 1.00 |
| Versicolor | 1.00 | 1.00 | 1.00 |
| Virginica | 1.00 | 1.00 | 1.00 |

No class showed lower performance than the others on the test set.
The results are homogeneous across all three classes.

However, these results were obtained on a small test set of 30 samples
and should not be interpreted as a guarantee of perfect performance
on new data.

## Ethical Considerations (Considérations éthiques)
The ethical risks associated with this model are limited because it is
designed for educational purposes and for classifying Iris flowers.

However, the model should not be used for high-stakes decision-making
or for applications involving people without appropriate validation.

The Iris dataset is small and may not represent the full diversity of
Iris flowers found in real-world conditions. This could introduce
limitations or biases when the model is applied to samples that differ
from the training data.

Users should therefore consider the representativeness of the dataset
before applying the model to other contexts.

## Caveats and Recommendations (Limites et recommandations)
The model was trained and evaluated on the small Iris dataset and may not
generalize well to samples that differ significantly from the training data.

The 100% accuracy obtained on the test set should be interpreted with caution,
as the evaluation was performed on only 30 samples.

Recommendations:
- Use this model primarily for educational and demonstration purposes.
- Validate the model on additional and representative data before using it
  in another context.
- Do not assume that the model will always achieve 100% accuracy on new data.
- Monitor model performance if it is applied to new datasets or environments.

## Reproductibility
The model can be reproduced using the provided training script and project
dependencies.

Steps to reproduce:

1. Install the project dependencies:

   `uv sync`

2. Run the training script:

   `uv run src/train.py`

The training script loads the Iris dataset, trains a RandomForestClassifier,
evaluates it on the test set, and saves the trained model to:

`model_artifacts/model.pkl`

The experiment uses 120 samples for training and 30 samples for testing.

### MLOps Traceability
The model training pipeline is linked to the following traceability metadata:

- **Model version:** iris-v1
- **MLflow run ID:** 4ac329e26aa84b666be481dbccebba412
- **Git SHA:** abc1234

These identifiers allow the trained model to be linked to its MLflow training run,
model version, and corresponding source-code revision.

## Audit & Monitoring

La traçabilité des prédictions, le mécanisme de journalisation et la
reconstitution d'une décision sont documentés séparément.

Voir : [Audit Trail](./audit_trail_README.md)

## AI Act Risk Classification

La classification du système au regard de l'AI Act est documentée séparément.

Voir : [Risk Classification](./risk_classification.md)
