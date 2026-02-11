# Algorithms

## Classification

Supervised learning algorithms that predict the class of an object.

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

### Evaluation

#### Confusion matrix

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

## Regression

Regression is a Supervised Learning task used to predict a continuous numeric value (e.g., price, temperature, or age).

### Linear Models

#### Linear Regression

- Regularization strength (Alpha/Lambda): Controls how much you penalize large coefficients to prevent overfitting.

- Fit Intercept: A boolean (True/False) determining whether to calculate the _b_ in: $y = mx + b$.

![Linear regression](./img/Linear_regression.png)

Multiple  regresion can include many variables:  $y = a + b_1x_1 + b_2x_2 + … + b_nx_n$.

![Polinomial regression](./img/Polinomial_regression.png)

##### Poisson Regression

- L1/L2 Regularization: Essential for stabilizing count predictions.

- Tolerance: The stopping criterion for the optimization algorithm.

### Tree-Based Regression

#### Decision Tree Regressor

- Max Depth: The most critical parameter. Limits how many "splits" the tree can make. Too deep = Overfitting.

- Min Samples Split: The minimum number of data points required to split an internal node.

#### Random Forest Regressor

- n_estimators: The number of trees in the forest. More trees increase stability but cost more compute.

- Max Features: The number of features to consider when looking for the best split.

#### Boosted Decision Tree (LightGBM)

- Learning Rate: How much each tree contributes to the final outcome. Usually between 0.01 and 0.3.

- Num Leaves: Controls the complexity of the tree. LightGBM is "leaf-wise," so this is more important than depth.

###  Specialized Regressors

#### Fast Forest Quantile Regression

- Quantiles: The specific percentiles you want to predict (e.g., 0.05, 0.5, 0.95).

#### Neural Network Regression

- Hidden Layer Architecture: Number of layers and nodes per layer.

- Learning Rate: How fast the weights are updated during training.

- Number of Iterations (Epochs): How many times the model sees the entire dataset.


### Regression Metrics

Regression is used when predicting a continuous numerical value (e.g., the price of a house or the temperature).

- **Mean Absolute Error (MAE)**: The average of the absolute differences between the predicted and actual values. It is easy to interpret as it is in the same units as the target.

- **Mean Squared Error (MSE)**: The average of the squared differences. This penalizes larger errors more heavily than smaller ones.

- **Root Mean Squared Error (RMSE)**: The square root of MSE. It brings the error metric back to the original units while still penalizing outliers.

- **R-Squared (R^2)**: Known as the "coefficient of determination." It represents the proportion of variance in the dependent variable that is predictable from the independent variables. An R^2 of 1.0 indicates a perfect fit.

### Comparison

| Algoritmo | Mejor usado para... | Complejidad del Modelo | Sensibilidad a Outliers | Característica Visual Clave |
| :--- | :--- | :--- | :--- | :--- |
| **Simple Linear Regression** | Relaciones directas y proporcionales entre dos variables. | Baja | Alta | Una línea recta que atraviesa una nube de puntos. |
| **Polynomial Regression** | Capturar relaciones curvas (ej. curvas de crecimiento). | Media | Alta | Una curva suave que puede tener múltiples dobleces. |
| **Support Vector Regression (SVR)** | Datasets complejos donde se busca ignorar el ruido menor. | Alta | Baja | Un "tubo" (épsilon-insensible) que encapsula los datos. |
| **Decision Tree Regression** | Capturar interacciones no lineales y cambios de "escalón". | Alta | Media | Una línea tipo "escalera" que sigue la tendencia de los datos. |
| **Random Forest Regression** | Predicciones de alto rendimiento en datasets grandes y complejos. | Muy Alta | Baja | Un conjunto de muchos árboles que suaviza los errores individuales. |
| **Ridge / Lasso Regression** | Prevenir el sobreajuste (overfitting) en modelos con muchas variables. | Media | Media | Similar a la lineal, pero la línea está "penalizada" para ser menos pronunciada. |