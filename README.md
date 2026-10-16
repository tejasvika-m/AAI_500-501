# Predicting Vehicle Fuel Efficiency Using the Auto MPG Dataset

**University of San Diego (USD)**  
**Course:** AAI 500 - Probability and Statistics for Artificial Intelligence  
**Project:** Final Team Project  
**Team:** Lernik Avetisyan and Tejasvika Mukundh

## 1. Project Overview

This completed project investigates how vehicle characteristics relate to fuel efficiency and how accurately they can be used to predict miles per gallon (MPG). Using the UCI Auto MPG dataset, the team cleaned and explored the data, compared two regression methods, selected a final model, and analyzed its predictive performance and limitations.

**Research question:** How accurately can vehicle characteristics predict a car's MPG, and which characteristics have the strongest relationship with fuel efficiency?

The complete, executed notebook is available at [`notebooks/Auto_MPG_Final_Project.ipynb`](notebooks/Auto_MPG_Final_Project.ipynb) and includes all six required project sections, code, saved outputs, tables, figures, and explanations.

## 2. Project Objectives

- Prepare the Auto MPG dataset for analysis and predictive modeling.
- Explore MPG distributions and relationships with vehicle characteristics.
- Compare Linear Regression with Random Forest Regression using training-only cross-validation.
- Evaluate the selected model on an untouched test set using R-squared, MAE, and RMSE.
- Examine prediction errors, residuals, and model-based feature importance.
- Summarize the findings, limitations, and recommendations.

## 3. Dataset

The project uses the [Auto MPG dataset](https://archive.ics.uci.edu/dataset/9/auto+mpg) from the UCI Machine Learning Repository. The dataset describes historical vehicle characteristics and city-cycle fuel efficiency.

**Target:** `mpg` (miles per gallon).

**Predictors:** `displacement`, `cylinders`, `horsepower`, `weight`, `acceleration`, `model_year`, and `origin`.

**Data preparation summary:**

| Item | Result |
| --- | ---: |
| Original observations | 398 |
| Predictor variables | 7 |
| Missing horsepower observations | 6 |
| Duplicate rows | 0 |
| Observations retained for modeling | 392 |
| Training observations | 313 |
| Testing observations | 79 |

The six records with missing horsepower were removed, leaving 392 complete observations for exploratory analysis and modeling. The `car_name` field was not used as a model predictor, but it was used with observed MPG to identify the most fuel-efficient vehicles. That descriptive ranking uses all **398 original observations**, including records excluded from modeling.

The notebook retrieves the data through the `ucimlrepo` Python package, so a separate dataset CSV is not required in this repository.

## 4. Methodology and Project Sections

### Section 1: Introduction and Data Loading
**Primary responsibility:** Lernik Avetisyan  
**Status:** Completed

The dataset is retrieved from UCI, its predictors and target are identified, and the analysis objective is introduced.

### Section 2: Data Cleaning and Preparation
**Primary responsibility:** Tejasvika Mukundh  
**Status:** Completed

The data are checked for missing values and duplicate rows. Six observations with missing horsepower are removed, resulting in 392 complete records.

### Section 3: Exploratory Data Analysis
**Primary responsibility:** Lernik Avetisyan  
**Status:** Completed

Descriptive statistics, an MPG histogram, scatterplots, a numerical correlation matrix, boxplots, and a model-year comparison are used to examine relationships between MPG and vehicle characteristics. The cleaned dataset has an average MPG of approximately **23.45**, with observed MPG ranging from **9.0 to 46.6**. The strongest negative correlations with MPG are weight (**-0.83**), displacement (**-0.81**), horsepower (**-0.78**), and cylinders (**-0.78**); model year has a positive correlation of approximately **0.58**.

### Section 4: Model Selection
**Primary responsibility:** Tejasvika Mukundh  
**Status:** Completed

The cleaned data are divided into training (80%) and testing (20%) sets using `random_state=42`. Linear Regression serves as a baseline, while Random Forest Regression can capture nonlinear relationships. The models are compared using shuffled **five-fold cross-validation on the training set only**. Preprocessing is fitted separately within each cross-validation training fold using pipelines; `origin` is treated as categorical and one-hot encoded. Random Forest achieves better cross-validation performance and is selected before evaluating the test set.

The final Random Forest uses `RandomForestRegressor(random_state=42)`, with its default 100 trees. No hyperparameter tuning is performed. Because MPG is a continuous numerical target, the task is regression and does not involve a classification threshold.

### Section 5: Model Analysis
**Primary responsibility:** Lernik Avetisyan  
**Status:** Completed

The selected Random Forest is evaluated on training and untouched test data. Actual-versus-predicted MPG and residual plots are examined, along with a feature-importance analysis. The training-to-testing performance gap suggests some overfitting, although the model maintains strong results on the test set.

### Section 6: Conclusion and Recommendations
**Primary responsibility:** Tejasvika Mukundh  
**Status:** Completed

The project summarizes model results, identifies influential predictors, discusses the most fuel-efficient vehicles by observed MPG, and outlines limitations and possible future improvements. Both team members reviewed the final notebook and technical report for consistency.

## 5. Models and Evaluation Results

Two models were evaluated with five-fold cross-validation on the training observations. The selected Random Forest was then fitted using the training data and assessed on the untouched test set.

| Evaluation | R-squared | MAE (MPG) | RMSE (MPG) |
| --- | ---: | ---: | ---: |
| Linear Regression, 5-fold cross-validation | 0.82 | 2.62 | 3.37 |
| Random Forest, 5-fold cross-validation | 0.86 | 2.04 | 2.87 |
| Random Forest, training | 0.98 | 0.76 | 1.09 |
| **Random Forest, testing** | **0.89** | **1.72** | **2.41** |

- **R-squared (R²):** Measures the proportion of variation in MPG explained by the model on the evaluated data.
- **Mean Absolute Error (MAE):** Measures the average absolute prediction error, in MPG.
- **Root Mean Squared Error (RMSE):** Measures prediction error while giving larger errors more weight.

The final model explains approximately **89% of the variation in test-set MPG** and has an average absolute test prediction error of **1.72 MPG**.

### Residual Analysis

Residuals are defined as **actual MPG minus predicted MPG**. For the Random Forest test predictions:

- Mean residual: **-0.37 MPG**, indicating slight average overprediction.
- Residual standard deviation: **2.40 MPG**.
- Largest absolute residual: **9.10 MPG**.

### Feature Importance

The Random Forest's five highest impurity-based feature-importance values are:

| Feature | Importance |
| --- | ---: |
| Displacement | 0.416 |
| Horsepower | 0.168 |
| Weight | 0.144 |
| Cylinders | 0.138 |
| Model year | 0.104 |

These values describe the predictors the fitted Random Forest relied on most. They do **not** establish causal effects and should not be interpreted as independent causal contributions, particularly where predictors are correlated.

## 6. Limitations and Future Work

- The dataset contains historical vehicles, so test performance on similar historical observations does not guarantee accuracy on modern vehicles.
- Removing only six incomplete records is a reasonable practical choice, but complete-case removal may introduce bias if missingness is systematic.
- Several vehicle characteristics are strongly correlated, complicating interpretation of individual feature-importance rankings.
- Impurity-based Random Forest importance can favor variables with more possible split values.
- The project compared two model types and used one final train/test split without hyperparameter tuning.

Future work could evaluate the model on newer vehicle data, include additional variables (such as transmission and fuel-system characteristics), compare more algorithms, and tune model parameters. The model may be useful as an initial estimation aid for vehicles similar to those represented in the dataset, rather than a validated predictor for every vehicle type.

## 7. Repository Structure

```text
AAI_500-501/
├── notebooks/
│   └── Auto_MPG_Final_Project.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

- `notebooks/Auto_MPG_Final_Project.ipynb`: Final executed notebook with all six sections, code, outputs, and visualizations.
- `README.md`: Project overview, methodology, results, limitations, and usage instructions.
- `requirements.txt`: Python dependencies for running the notebook.
- `.gitignore`: Excludes common temporary or environment-specific files from version control.
- `LICENSE`: Repository license (MIT).

The complete technical report PDF and recorded presentation MP4 are separate final deliverables submitted through Canvas.

## 8. Notebook Access and Setup

The project was developed using Python in Google Colab/Jupyter Notebook.

1. Open [`notebooks/Auto_MPG_Final_Project.ipynb`](notebooks/Auto_MPG_Final_Project.ipynb) in Google Colab or a Jupyter environment.
2. Install the repository's dependencies, if needed:

   ```bash
   pip install -r requirements.txt
   ```

   In Google Colab, the notebook also includes a command to install `ucimlrepo`.
3. Run all notebook cells **in order**, starting from the data-loading step. Internet access is needed to retrieve the UCI dataset on a fresh run.
4. Review the displayed tables, figures, model comparison, evaluation metrics, and conclusions.

Saved outputs are included for inspection without rerunning the notebook. Minor differences can occur across dependency versions or environments; the reported results are those obtained in the project's verified notebook.

## 9. Team Members and Contributions

**Lernik Avetisyan:** Sections 1, 3, and 5 (Introduction and Data Loading; Exploratory Data Analysis; Model Analysis).

**Tejasvika Mukundh:** Sections 2, 4, and 6 (Data Cleaning and Preparation; Model Selection; Conclusion and Recommendations).

Both team members reviewed the notebook, technical report, and presentation for consistency.

## 10. Reference

Quinlan, R. (1993). *Auto MPG* [Data set]. UCI Machine Learning Repository. https://doi.org/10.24432/C5859H
