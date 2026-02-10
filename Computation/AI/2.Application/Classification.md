# Classification

Supervised learning algorithms that predict the class of an object.

## Algorithms

### Linear Models

#### Logistic Regression

- Regularization strength (C): Controls overfitting. A smaller value of C means stronger regularization (more penalty on large weights).

- Penalty (L1 or L2): Defines the type of regularization. L1 (Lasso) can lead to sparse models (some weights become zero), while L2 (Ridge) keeps all features but shrinks their influence.

#### Support Vector Machines (SVM)

- C (Penalty): The trade-off between having a wide margin and correctly classifying all training points.

- Kernel: Defines the decision boundary shape (Linear, Polynomial, RBF).

- Gamma: Specific to kernels like RBF; it defines how far the influence of a single training example reaches.

### Tree-Based Models (High Priority for the Exam)

#### Decision Tree
 
- Max Depth: The maximum number of levels in the tree. Too high leads to overfitting; too low leads to underfitting.
  
- Min Samples Leaf: The minimum number of samples a terminal node (leaf) must have. Higher values prevent the model from learning _noise_.

#### Random Forest

- Number of Estimators: The number of individual trees in the "forest." More trees generally improve performance but increase computation time.

- Max Features: The number of features considered when looking for the best split at each node.

#### Gradient Boosted Models (LightGBM, XGBoost)

- Learning Rate: Determines the impact of each new tree on the final result. Lower values (e.g., 0.01) usually yield better models but require more trees.

- Number of Iterations / Boosting Rounds: The number of sequential trees built to correct the errors of previous ones.

### Other

#### K-Nearest Neighbors (KNN)

- Number of Neighbors (K): The number of nearby data points the model looks at to make a decision. A small K makes the model sensitive to noise; a large K makes it more "smooth" but potentially less precise.

- Distance Metric: The formula used to calculate "closeness" between points (e.g., Euclidean for straight-line distance or Manhattan for city-block distance).

#### Neural Networks

- Learning Rate: Crucial for convergence. It determines the size of the steps the model takes while searching for the minimum error.

- Batch Size: The number of training examples processed before the internal model parameters are updated.

- Hidden Layers / Nodes: The "architecture." More layers (depth) and nodes (width) allow the model to learn more complex patterns but increase the risk of overfitting.

#### Naive Bayes

- Smoothing (Alpha): Used to handle cases where a category has zero probability in the training data (prevents the whole calculation from becoming zero).

## Evaluation

### Confusion matrix

|Actual/Prediction|False|True|
|-|-|-|
|False|TN|FP (Error 1)|
|True|FN (Error 2)|TP|

### Metrics

- **Accuracy**: The ratio of correct predictions to total predictions. It is often misleading if the dataset is imbalanced (e.g., 99% of samples are "Healthy").

```Accuracy=TP/All```

- **Precision**: Out of all predicted positives, how many were actually positive? (Focuses on avoiding False Positives).

```Precision=TP/Predicted positives=TP/TP+Error 1```

- **Recall (Sensitivity)**: Out of all actual positives, how many did the model find? (Focuses on avoiding False Negatives).

```Recall=TP/Actual positives=TP/TP+Error 2```

- **F1-Score**: The harmonic mean of Precision and Recall. It provides a single score that balances both, especially useful for imbalanced data.

```F1=2(precision.recall/precision+recall)```

- **AUC-ROC**: Measures the model's ability to distinguish between classes at various threshold levels.

![AU-ROC](img/auc-roc.png)