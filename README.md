# Data Science Notebooks

A sequence of self-contained Jupyter notebooks covering data science (for KU's ENG-500) with Python, from language
fundamentals through machine learning, deep learning, time series, and model explainability.

The notebooks are numbered in teaching order. Each one builds on ideas from the previous, but every
notebook runs on its own. They were authored in Google Colab and run there without any setup.

## Notebooks

| # | Notebook | Contents |
|---|----------|----------|
| 00 | [00_DataScienceDemo.ipynb](00_DataScienceDemo.ipynb) | End-to-end walkthrough of a small project: loading the California housing data, exploring it, handling missing values, and plotting distributions. |
| 01 | [01_PythonFundamentals.ipynb](01_PythonFundamentals.ipynb) | Python primer — variables and types, control flow, functions, iterables, error handling, comprehensions and lambdas, file I/O, f-strings. |
| 02 | [02_NumPyFundamentals.ipynb](02_NumPyFundamentals.ipynb) | Array creation and attributes, indexing and slicing, reshaping, arithmetic and broadcasting, aggregations, linear algebra, random number generation. |
| 03 | [03_UsingPandas.ipynb](03_UsingPandas.ipynb) | Series and DataFrames, loading and saving, inspection, selection and indexing, cleaning, `groupby` aggregation, merges and joins, pivots, time series basics. |
| 04 | [04_DataPreprocessing.ipynb](04_DataPreprocessing.ipynb) | Missing values (removal vs. imputation), duplicates, type conversion, data integration, min-max and standard scaling, equal-width and equal-frequency binning. |
| 05 | [05_ExploratoryDataAnalysis.ipynb](05_ExploratoryDataAnalysis.ipynb) | Distribution shapes, statistical measures, visual EDA, and correlation analysis. |
| 06 | [06_DimensionalityReduction.ipynb](06_DimensionalityReduction.ipynb) | Filter-based feature selection with correlation coefficients and a variance threshold; feature extraction with PCA. |
| 07 | [07_MachineLearningPipeline.ipynb](07_MachineLearningPipeline.ipynb) | A full pipeline: train/validation/test splitting, training and validating a random forest, test-set evaluation, and visualizing predictions. |
| 08 | [08_SupervisedLearning.ipynb](08_SupervisedLearning.ipynb) | Regression and classification on synthetic datasets, with exercises and discussion of the findings. |
| 09 | [09_NeuralNetworks.ipynb](09_NeuralNetworks.ipynb) | Keras/TensorFlow models for regression, classification (with a decision-boundary plot), an RNN for sequences, and a CNN for images. |
| 10 | [10_TimeSeries.ipynb](10_TimeSeries.ipynb) | Forecasting AAPL prices: naive, average and drift baselines, ARIMA, exponential smoothing, then random forest, XGBoost, and LSTM, compared side by side. |
| 11 | [11_XAI.ipynb](11_XAI.ipynb) | Explainable AI — LIME, DiCE counterfactuals, SHAP (global and local), permutation feature importance, and 1-way/2-way partial dependence plots. |
| 12 | [12_Visualization.ipynb](12_Visualization.ipynb) | A gallery of Seaborn plots (scatter, line, bar, histogram, box, violin, heatmap, pair) and interactive Plotly charts (including 3D scatter, sunburst, sliders, and dropdown filtering). |

## Running the notebooks

### Google Colab (recommended)

No installation needed — open a notebook from GitHub in Colab, e.g.:

```
https://colab.research.google.com/github/KU-ENG500/datascience_notebooks/blob/main/02_NumPyFundamentals.ipynb
```

Swap the filename at the end of the URL for any other notebook in the table above. Notebooks that
need extra packages install them in their first cell.

### Locally

```bash
git clone https://github.com/KU-ENG500/datascience_notebooks.git
cd datascience_notebooks

python -m venv .venv
source .venv/bin/activate       # Windows: .venv\Scripts\activate

pip install jupyter numpy pandas matplotlib seaborn plotly scikit-learn
jupyter notebook
```

The later notebooks need additional packages:

| Notebook | Extra packages |
|----------|----------------|
| 09, 10 | `tensorflow` |
| 10 | `yfinance`, `pmdarima`, `statsmodels`, `xgboost` |
| 11 | `lime`, `shap`, `dice-ml` |

Install them all at once with:

```bash
pip install tensorflow yfinance pmdarima statsmodels xgboost lime shap dice-ml
```

## Data

Most notebooks generate their own data with NumPy or scikit-learn's synthetic data generators
(`make_regression`, `make_classification`, `make_moons`). The rest download what they need at
runtime: notebook 10 pulls AAPL prices via `yfinance`, and notebooks 05, 07, and 11 fetch CSVs over
HTTP — those cells need a network connection.

The [sample_data/](sample_data/) directory holds Colab's standard sample datasets plus one extra:

- `california_housing_train.csv` / `california_housing_test.csv` — used by notebook 00
- `anscombe.json` — Anscombe's quartet
- `mnist_test.csv` — MNIST test split
- `dirty_cafe_sales.csv` — cafe transactions with missing and `ERROR` values, useful for practicing the cleaning steps in notebook 04

## Requirements

Python 3.10 or newer.
