
## 1. Evaluation Metrics

- **Accuracy**
  - Definition: The ratio of correctly predicted instances to the total instances.
  - Strengths: Simple and easy to interpret.
  - Limitations: Misleading in imbalanced datasets where one class dominates.
  - Example: A model predicting all instances as the majority class can achieve high accuracy but fail to capture minority class instances.

- **Precision**
  - Definition: The ratio of true positive predictions to the total predicted positives.
  - Formula: 
		\( $\text{Precision} = \frac{\text{TP}}{\text{TP} + \text{FP}}$ \).
  - Use Case: Important when false positives are costly (e.g., spam detection).
  - Example: In fraud detection, precision ensures minimal misclassification of legitimate transactions as fraudulent.

- **Recall (Sensitivity or True Positive Rate)**
  - Definition: The ratio of true positive predictions to the total actual positives.
  - Formula: \( $\text{Recall} = \frac{\text{TP}}{\text{TP} + \text{FN}}$ \).
  - Use Case: Critical when missing a positive instance has high consequences (e.g., disease detection).
  - Example: In cancer diagnosis, recall focuses on identifying all cancer-positive cases.

- **F1-Score**
  - Definition: Harmonic mean of precision and recall, balancing both metrics.
  - Formula: \( $F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$ \).
  - Use Case: Suitable when precision and recall are equally important.
  - Example: Useful in cases where class distribution is imbalanced.

- **Confusion Matrix**
  - Components:
    - True Positive (TP): Correctly identified positive cases.
    - True Negative (TN): Correctly identified negative cases.
    - False Positive (FP): Incorrectly identified negative as positive.
    - False Negative (FN): Incorrectly identified positive as negative.
  - Applications: A foundational tool for evaluating model predictions.
  - Example: A two-class confusion matrix provides a clear snapshot of prediction errors.

- **ROC Curves and AUC**
  - **ROC Curve**:
    - Definition: A graph showing the trade-off between true positive rate (recall) and false positive rate at various thresholds.
    - Use: Visualizes the classifier’s ability to distinguish between classes.
  - **AUC (Area Under the Curve)**:
    - Definition: A single scalar value summarizing the ROC curve.
    - Interpretation: Higher AUC indicates better classifier performance.
    - Example: An AUC close to 1 signifies a model with near-perfect separability.

## 2. Model Comparison

- **Methods for Model Comparison**
  - Cross-validation:
    - Definition: Splitting the dataset into training and validation sets multiple times to evaluate consistency.
    - Benefit: Provides reliable performance metrics by reducing variance due to dataset splits.
  - Metrics-based comparison:
    - Comparing models using metrics like accuracy, precision, recall, F1-score, and AUC.
  - Statistical significance tests:
    - Techniques such as paired t-tests to ensure observed differences between models are not due to chance.

- **Limitations of Specific Metrics**
  - Accuracy:
    - Misleading in imbalanced datasets where it may favor majority class predictions.
    - Example: In a dataset with 99% of one class, predicting only the majority class achieves 99% accuracy.
  - Precision vs. Recall Trade-offs:
    - High precision may reduce recall and vice versa.
    - Example: Increasing spam filters’ precision may miss legitimate emails (lower recall).
  - F1-Score:
    - May not fully capture the relative importance of precision and recall in some cases.
    - Example: F1-score does not differentiate cases where precision is more important than recall or vice versa.

- **Use of Cost-Sensitive Metrics**
  - Cost Matrix:
    - Assigning weights to different types of prediction errors (e.g., FP vs. FN) based on their impact.
    - Example: In credit card fraud detection, a false positive (blocking legitimate transactions) may have a lower cost than a false negative (missing fraud).
