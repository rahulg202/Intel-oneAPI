# Intel-oneAPI
# OneAPI Water Quality Analysis

This repository contains scripts to analyze water quality datasets using Intel's oneAPI Data Analytics Library (oneDAL) and traditional Python libraries like Pandas, Matplotlib, and Seaborn.

![Water Quality Prediction](https://github.com/Aditya3012Purwar/Intel-oneAPI/assets/103439955/11e84689-5ab6-48e9-aaf2-fc4e012bdc98)


## Installation

To run these scripts, you will need to install the necessary libraries. The primary library used here is `scikit-learn-intelex` which is an extension of Scikit-learn powered by Intel(R) oneAPI Data Analytics Library. Install it using:

```bash
pip install scikit-learn-intelex
```

## Overview

The analysis starts with loading a dataset containing water quality attributes. Each record represents a water sample and contains attributes like pH, Iron concentration, Turbidity, Chloride, and many others. The goal is to explore this dataset and possibly prepare it for further machine learning tasks.

### Main Steps:

1. **Enable Intel(R) Extension for Scikit-learn**:
   This step patches the original Scikit-learn to use Intel(R) oneAPI Data Analytics Library as the backend.
   
   ```python
   from sklearnex import patch_sklearn
   patch_sklearn()
   ```

2. **Data Loading**:
   The dataset is loaded using Pandas. The dataset contains over 5 million rows and 24 columns.
   
   ```python
   import pandas as pd
   dataset = pd.read_csv('/path_to_dataset/dataset.csv')
   ```

3. **Basic Data Exploration**:
   - Checking the shape of the dataset.
   - Listing the columns.
   - Getting information about the data types and number of non-null values.
   - Checking the summary statistics.

4. **Visualization**:
   A heatmap is created to visualize the correlation between different numerical columns in the dataset.
   
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns
   correlation_matrix = dataset.corr(numeric_only=True)
   plt.figure(figsize=(20, 20))
   sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f", square=True)
   plt.title('Correlation Heatmap')
   plt.show()
   ```

5. **Data Cleaning**:
   - Deleting unwanted columns.
   - Handling missing values.

6. **Data Transformation**:
   Textual data in the dataset are mapped to numerical values for easier processing in machine learning tasks. Specifically, the 'Color' and 'Source' columns are converted to numerical values based on their unique entries.

## Dataset Columns

Here's a brief overview of some of the columns:

- **pH**: pH level of the water.
- **Iron, Nitrate, Chloride, ...**: Different chemical concentrations.
- **Color**: Color classification of the water.
- **Turbidity**: Cloudiness or haziness of the water.
- **Source**: The source from where the water sample is taken.
- **Target**: This might be the label if the dataset is used for classification tasks. (0 or 1)

## Conclusion

This script serves as an initial exploratory data analysis of the water quality dataset. Based on the observations from this script, further preprocessing or feature engineering can be applied to prepare the dataset for machine learning models.
