# Machine Learning Assignment

**Author:** Avi Singh

A collection of nine Jupyter notebooks implementing core supervised and unsupervised machine learning algorithms in Python with `scikit-learn`. Six notebooks operate on an included housing dataset (`house_price_dataset.csv`), while the remaining three use built-in `scikit-learn` datasets (Breast Cancer Wisconsin and Iris).

## Project Structure

```text
.
├── house_price_dataset.csv
├── Simple_linear_regression.ipynb
├── Multiple_Linear_regression.ipynb
├── Regression_model_regularization.ipynb
├── Logistic_regression.ipynb
├── SVM.ipynb
├── Decision_Tree.ipynb
├── Naive_Bayes.ipynb
├── K_Mean_Clustring.ipynb
└── PCA.ipynb
```

## Datasets

| Dataset | Source | Dimensions | Target / Task | Used In |
| :--- | :--- | :--- | :--- | :--- |
| House Price Dataset | `house_price_dataset.csv` | 15,025 rows × 18 columns | `Price` (regression), median-split binary class (classification), feature compression (PCA) | `Simple_linear_regression.ipynb`, `Multiple_Linear_regression.ipynb`, `Regression_model_regularization.ipynb`, `Logistic_regression.ipynb`, `SVM.ipynb`, `PCA.ipynb` |
| Breast Cancer Wisconsin | `sklearn.datasets.load_breast_cancer` | 569 rows × 30 numeric features | Binary diagnosis (`malignant`: 212, `benign`: 357) | `Decision_Tree.ipynb` |
| Iris | `sklearn.datasets.load_iris` | 150 rows × 4 numeric features | 3 flower species (`setosa`, `versicolor`, `virginica`, 50 each) | `Naive_Bayes.ipynb`, `K_Mean_Clustring.ipynb` |

### House Price Dataset Details (`house_price_dataset.csv`)

- **Identifier (excluded from modeling):** `House_ID`
- **Numerical Features (10):** `Area_sqft`, `Bedrooms`, `Bathrooms`, `Floors`, `Year_Built`, `Garage_Count`, `Lot_Size_sqft`, `Distance_to_City_Center_km`, `Crime_Rate_Index`, `School_Rating`
- **Categorical Features (6):** `Location`, `Furnishing_Status`, `Parking_Available`, `Condition`, `Has_Pool`, `Renovated`
- **Target Variable:** `Price` (min: `20,000`, median: `359,454`, mean: `369,062.82`, max: `926,035`)
- **Missing Data:** 11 feature columns contain missing values (ranging from 300 in `Bathrooms`, `Garage_Count`, and `Distance_to_City_Center_km` up to 1,051 in `School_Rating`); `Price` has no missing values. Multi-feature pipelines handle these using `SimpleImputer` (median for numerical columns, most frequent for categorical columns).

## Summary of Models and Results

### Regression Models (`house_price_dataset.csv` — Target: `Price`)

| Notebook | Model | Train / Test Split | MAE | RMSE | R² Score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `Simple_linear_regression.ipynb` | Linear Regression (`Area_sqft` only) | 11,537 / 2,885 | 57,929.90 | 72,952.82 | 0.6698 |
| `Multiple_Linear_regression.ipynb` | Linear Regression (16 features) | 12,020 / 3,005 | 30,111.18 | 42,126.37 | 0.8965 |
| `Regression_model_regularization.ipynb` | Linear Regression (scaled) | 12,020 / 3,005 | 30,119.04 | 42,119.68 | 0.8965 |
| `Regression_model_regularization.ipynb` | Ridge (`alpha=1.0`) | 12,020 / 3,005 | 30,121.68 | 42,124.77 | 0.8965 |
| `Regression_model_regularization.ipynb` | Lasso (`alpha=0.01`, `max_iter=10000`) | 12,020 / 3,005 | 30,119.04 | 42,119.69 | 0.8965 |

### Classification Models

| Notebook | Model | Dataset | Train / Test Split | Accuracy | Macro F1 | ROC-AUC |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `Logistic_regression.ipynb` | Logistic Regression (`max_iter=1000`) | House Price (median split) | 12,020 / 3,005 | 0.9105 | 0.91 | 0.9722 |
| `SVM.ipynb` | Linear SVM (`kernel="linear"`, `C=1.0`) | House Price (median split) | 12,020 / 3,005 | 0.9125 | 0.91 | 0.9725 |
| `SVM.ipynb` | RBF SVM (`kernel="rbf"`, `C=1.0`, `gamma="scale"`) | House Price (median split) | 12,020 / 3,005 | 0.8982 | 0.90 | 0.9645 |
| `Decision_Tree.ipynb` | Decision Tree (`criterion="gini"`, `max_depth=4`) | Breast Cancer Wisconsin | 455 / 114 | 0.9386 | 0.93 | — |
| `Naive_Bayes.ipynb` | Gaussian Naive Bayes (`GaussianNB`) | Iris | 120 / 30 | 0.9667 | 0.97 | — |

### Unsupervised Learning Models

| Notebook | Technique | Dataset | Key Configuration | Recorded Output |
| :--- | :--- | :--- | :--- | :--- |
| `K_Mean_Clustring.ipynb` | K-Means Clustering | Iris (standardized) | `n_clusters=3`, `n_init=10`, `random_state=42` | Inertia: `139.8205`, Silhouette: `0.4599`, ARI: `0.6201` |
| `PCA.ipynb` | Principal Component Analysis | House Price (80 encoded features, standardized) | Retain ≥ 95% cumulative variance | 70 components (`95.34%` variance retained, `12.5%` reduction) |

## Notebook Breakdown

### 1. `Simple_linear_regression.ipynb`
Models `Price` as a linear function of `Area_sqft` alone after dropping rows with missing values in either column (leaving 14,422 rows). Fits `LinearRegression` on an 80/20 split (`random_state=42`), producing the fitted equation `Predicted Price = 79530.40 + (132.21 × Area_sqft)`. Includes an actual-vs-fitted regression line scatter plot and a sample prediction for a 2,000 sq. ft. house (`343,947.52`).

### 2. `Multiple_Linear_regression.ipynb`
Uses all 16 housing features with a `ColumnTransformer` preprocessing pipeline (median imputation for numerical columns; most-frequent imputation and `OneHotEncoder(handle_unknown="ignore")` for categorical columns). Evaluates MAE, MSE, RMSE, and R², plots actual vs. predicted prices, inspects the top 15 feature coefficients by absolute magnitude, and predicts a sample listing.

### 3. `Regression_model_regularization.ipynb`
Compares standard `LinearRegression`, `Ridge(alpha=1.0)`, and `Lasso(alpha=0.01, max_iter=10000)` on `house_price_dataset.csv` using median imputation + `StandardScaler` for numerical features and most-frequent imputation + `OneHotEncoder` for categorical features. Evaluates all three models side by side, plots an R² bar chart and a 50-sample actual-vs-predicted line chart, and compares learned coefficients (Lasso shrinks 1 coefficient to zero at `alpha=0.01`).

### 4. `Logistic_regression.ipynb`
Converts `Price` into a balanced binary target `High_Price` (`0` = below median `359,454.0` with 7,512 rows; `1` = at or above median with 7,513 rows). Trains a `LogisticRegression(max_iter=1000)` pipeline on a stratified 80/20 split and evaluates accuracy, classification report, ROC-AUC, a confusion matrix heatmap, an ROC curve, and sample class probabilities.

### 5. `SVM.ipynb`
Uses the same median-threshold binary classification target (`Price_Category`) and stratified 80/20 split as Logistic Regression to compare `SVC(kernel="linear", C=1.0)` against `SVC(kernel="rbf", C=1.0, gamma="scale", probability=True, random_state=42)`. Outputs side-by-side confusion matrices, ROC curves, classification reports, and sample predictions.

### 6. `Decision_Tree.ipynb`
Trains a `DecisionTreeClassifier(criterion="gini", max_depth=4, random_state=42)` on the Breast Cancer Wisconsin dataset using a stratified 80/20 split. Visualizes the confusion matrix, the full decision tree (`plot_tree`), and the top 10 most important features (`worst radius` at `0.7335` and `worst concave points` at `0.1220` account for most of the split importance).

### 7. `Naive_Bayes.ipynb`
Trains a `GaussianNB` classifier on the Iris dataset with a stratified 80/20 split. Evaluates accuracy (`96.67%`), per-class precision/recall/F1, plots a confusion matrix and a `seaborn` feature pairplot colored by species, and prints predicted class probabilities for a sample flower.

### 8. `K_Mean_Clustring.ipynb`
Standardizes the 4 Iris features with `StandardScaler` and applies `KMeans(n_clusters=3, random_state=42, n_init=10)`. Evaluates Inertia, Silhouette Score, and Adjusted Rand Index against known species labels, displays a species-vs-cluster crosstab (Cluster 1 isolates all 50 `setosa` samples), projects clusters into 2D via PCA (`95.81%` variance retained), and plots an Elbow Method curve for `K = 1` to `10`.

### 9. `PCA.ipynb`
Applies median/mode imputation, one-hot encoding (expanding 16 columns into 80 features), and `StandardScaler` to `house_price_dataset.csv`. Computes full PCA explained variance ratios, plots scree and cumulative variance curves with a 95% threshold line, reduces the dataset from 80 to 70 principal components (`95.34%` variance retained), and plots the first two principal components.

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook, JupyterLab, or VS Code with the Jupyter extension

### Installation

Install the required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Running the Notebooks

1. Ensure `house_price_dataset.csv` is in the same working directory as the `.ipynb` files (the six housing notebooks load it via `pd.read_csv("house_price_dataset.csv")`).
2. Launch Jupyter from the project root:

```bash
jupyter notebook
```

3. Open any notebook and run all cells sequentially.

## Implementation Notes

- **Categorical Text Variations:** Categorical columns in `house_price_dataset.csv` contain mixed casing, whitespace, and spelling variants (for example, `Downtown`, `DOWNTOWN`, `downtown`, and ` Downtown` in `Location`, or `Good`/`good`/`Gud` in `Condition`). The notebooks encode these categories directly without string normalization, which expands the 16 raw features to 80 one-hot encoded columns.
- **Scikit-Learn Deprecation Notice:** In `SVM.ipynb`, `SVC(probability=True)` triggers a `FutureWarning` in newer `scikit-learn` releases recommending `CalibratedClassifierCV(SVC(), ensemble=False)` for probability estimation.
- **Notebook Utility Cell:** `Decision_Tree.ipynb` contains a cell (`del display; from IPython.display import display`) that resets `display` if it was shadowed during interactive execution; if running cleanly from top to bottom in a fresh kernel, that `del display` line may raise a `NameError` unless removed or skipped.

## Author & Credits

- **Author:** Avi Singh (`avisingh6382@gmail.com`)
- **Datasets:** Included `house_price_dataset.csv`, plus the Breast Cancer Wisconsin (Diagnostic) and Iris datasets bundled with `scikit-learn` (`sklearn.datasets`).
- **Libraries & Tools:** Built with Python, `scikit-learn`, `pandas`, `NumPy`, `Matplotlib`, `Seaborn`, and Jupyter Notebook.