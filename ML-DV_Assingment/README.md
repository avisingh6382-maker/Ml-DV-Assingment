# Machine Learning & Data Visualization Assignment (`ml_dv_assingment`)

**Author:** Avi Singh

This repository brings together two coursework assignments organized into dedicated folders:
- **`ml/`** — Nine Python / Jupyter notebooks implementing supervised and unsupervised machine learning algorithms with `scikit-learn` on a custom housing dataset (`house_price_dataset.csv`) and built-in datasets (Breast Cancer Wisconsin and Iris).
- **`dv/`** — Eight Microsoft Power BI (`.pbix`) experiments covering data preparation, comparative charts, interactive dashboards, geospatial mapping, part-to-whole visuals, heatmaps/treemaps, and time-series forecasting.

## Repository Structure

```text
ml_dv_assingment/
├── README.md
├── ml/
│   ├── README.md
│   ├── house_price_dataset.csv
│   ├── Simple_linear_regression.ipynb
│   ├── Multiple_Linear_regression.ipynb
│   ├── Regression_model_regularization.ipynb
│   ├── Logistic_regression.ipynb
│   ├── SVM.ipynb
│   ├── Decision_Tree.ipynb
│   ├── Naive_Bayes.ipynb
│   ├── K_Mean_Clustring.ipynb
│   └── PCA.ipynb
└── dv/
    ├── README.md
    ├── Experiment 1.pbix
    ├── Experiment 2.pbix
    ├── Experiment 3.pbix
    ├── Experiment 4.pbix
    ├── experiment 5.pbix
    ├── Experiment 6.pbix
    ├── Experiment 7.pbix
    └── Experiment 8.pbix
```

For full per-assignment documentation, see [ml/README.md](https://www.google.com/search?q=ml/README.md) and [dv/README.md](https://www.google.com/search?q=dv/README.md).

## Assignment Overview

### 1. Machine Learning (`ml/`)

Implements end-to-end preprocessing pipelines, model training, evaluation, and visualization across regression, classification, clustering, and dimensionality reduction.

| Category | Notebook | Dataset | Key Result |
| :--- | :--- | :--- | :--- |
| Regression | `Simple_linear_regression.ipynb` | `house_price_dataset.csv` (`Area_sqft`) | R²: `0.6698`, RMSE: `72,952.82` |
| Regression | `Multiple_Linear_regression.ipynb` | `house_price_dataset.csv` (16 features) | R²: `0.8965`, RMSE: `42,126.37` |
| Regression | `Regression_model_regularization.ipynb` | `house_price_dataset.csv` (Linear, Ridge, Lasso) | R²: `0.8965` across all three models |
| Classification | `Logistic_regression.ipynb` | `house_price_dataset.csv` (median split) | Accuracy: `0.9105`, ROC-AUC: `0.9722` |
| Classification | `SVM.ipynb` | `house_price_dataset.csv` (Linear vs. RBF) | Linear Acc: `0.9125` (AUC `0.9725`); RBF Acc: `0.8982` |
| Classification | `Decision_Tree.ipynb` | Breast Cancer Wisconsin | Accuracy: `0.9386`, Macro F1: `0.93` |
| Classification | `Naive_Bayes.ipynb` | Iris | Accuracy: `0.9667`, Macro F1: `0.97` |
| Clustering | `K_Mean_Clustring.ipynb` | Iris (standardized) | Silhouette: `0.4599`, ARI: `0.6201` |
| Dimensionality Reduction | `PCA.ipynb` | `house_price_dataset.csv` (80 encoded features) | 70 components retain `95.34%` variance |

### 2. Data Visualization (`dv/`)

Implements eight progressive Power BI Desktop experiments covering visual encoding, interactivity, spatial analytics, and forecasting.

| Experiment | Data Model Table | Visuals & Features |
| :--- | :--- | :--- |
| `Experiment 1.pbix` | `Superstore_Sales_Experiment1` | Clustered column chart (`Category`) and dual-axis line chart (`Order Date` hierarchy) for Sales & Profit |
| `Experiment 2.pbix` | `PowerBI_Experiment2_Raw_Sales_Data` | Raw sales data loading and Power Query preparation (data model only) |
| `Experiment 3.pbix` | `PowerBI_Experiment3_Sales_TimeSeries` | Regional Sales column chart and multi-series Profit time-series line chart |
| `Experiment 4.pbix` | `PowerBI_Experiment3_Sales_TimeSeries` | Interactive dashboard with 3 slicers (`Category`, `Region`, `Date`), 2 KPI cards, and trend line chart |
| `experiment 5.pbix` | `PowerBI_Experiment5_Geo_Sales_Data` | *"Sales Distribution across India"* bubble map (`Latitude`/`Longitude`) and City sales bar chart |
| `Experiment 6.pbix` | `PowerBI_Experiment6_Olympic_Medals` | Pie chart and Donut chart comparing `Total Medals` by `Country` |
| `Experiment 7.pbix` | `PowerBI_Experiment7_Heatmap_Treemap` | Conditional-gradient Matrix heatmap (`Region` × `Category`) and `Category`/`Subcategory` Treemap |
| `Experiment 8.pbix` | `PowerBI_Experiment8_TimeSeries_Forecasting` | *"Monthly Sales Trend"* line chart with trend line and 3-period forecast (95% confidence) |

## Getting Started

### Running the Machine Learning Notebooks (`ml/`)

1. Ensure Python 3.8+ is installed and install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

2. Navigate into the `ml/` directory (so notebooks can read `house_price_dataset.csv` via relative path) and launch Jupyter:

```bash
cd ml
jupyter notebook
```

### Viewing the Data Visualization Reports (`dv/`)

1. Install **Microsoft Power BI Desktop**.
2. Open any `.pbix` file inside the `dv/` directory directly in Power BI Desktop to explore visuals, slicers, date drill-downs, and forecasting panes.

## Author & Credits

- **Author:** Avi Singh (`avisingh6382@gmail.com`)
- **Machine Learning Stack:** Python, `scikit-learn`, `pandas`, `NumPy`, `Matplotlib`, `Seaborn`, and Jupyter Notebook (`house_price_dataset.csv`, plus `scikit-learn`'s Breast Cancer Wisconsin and Iris datasets).
- **Data Visualization Stack:** Microsoft Power BI Desktop with embedded experiment datasets across Experiments 1–8.
