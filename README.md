# Predicting Vehicle Fuel Efficiency Using the Auto MPG Dataset

**University of San Diego (USD)**  
**Course:** AAI 500 - Probability and Statistics for Artificial Intelligence  
**Project:** Final Team Project

## 1. Project Overview

This project examines the relationship between vehicle characteristics and fuel efficiency using the UCI Auto MPG dataset. The objective is to conduct a statistical analysis of the dataset and develop regression models that predict vehicle fuel efficiency, measured in miles per gallon (MPG).

The project includes data preparation, exploratory data analysis, predictive modeling, model evaluation, and interpretation of the findings.

**Current status:** The working Jupyter notebook includes Sections 1–3. Sections 4–6 will be added as the project progresses.

## 2. Project Objectives

The main objectives of this project are to:

- Prepare the Auto MPG dataset for statistical analysis.
- Examine how vehicle characteristics relate to fuel efficiency.
- Identify patterns and relationships through descriptive statistics and visualizations.
- Develop and compare Linear Regression and Random Forest Regression models.
- Evaluate predictive performance using appropriate regression metrics.
- Interpret the findings, discuss limitations, and develop conclusions and recommendations.

## 3. Dataset

This project uses the [Auto MPG dataset](https://archive.ics.uci.edu/dataset/9/auto+mpg) from the UCI Machine Learning Repository.

The dataset contains information about vehicle characteristics and city-cycle fuel consumption.

**Target variable:** Miles per gallon (MPG).

**Predictor variables:**
- Cylinders
- Displacement
- Horsepower
- Weight
- Acceleration
- Model year
- Origin

The dataset contains 398 observations. During data preparation, six observations with missing horsepower values were removed, leaving 392 observations for the subsequent analysis.

The dataset is retrieved directly from the UCI Machine Learning Repository using the Python `ucimlrepo` library. Therefore, no separate dataset files are stored in this repository.

## 4. Methodology

The project is organized into six sections, with responsibilities divided equally between both team members. Each team member is responsible for three sections, and both members are expected to participate in coding and reviewing the project.

### Section 1: Introduction and Data Loading

**Responsible:** Lernik Avetisyan  
**Status:** Completed

The dataset is retrieved from the UCI Machine Learning Repository, and its structure, variables, and initial characteristics are examined.

### Section 2: Data Cleaning and Preparation

**Responsible:** Tejasvika Mukundh  
**Status:** Completed

The dataset is inspected for missing values, duplicate observations, and data quality issues. Observations with missing horsepower values are removed, and the prepared dataset is used for subsequent analysis.

### Section 3: Exploratory Data Analysis

**Responsible:** Lernik Avetisyan  
**Status:** Completed

Descriptive statistics and visualizations are used to explore the dataset, examine the distribution of MPG, investigate relationships between vehicle characteristics and fuel efficiency, and identify patterns that may be relevant to predictive modeling.

### Section 4: Model Selection

**Responsible:** Tejasvika Mukundh  
**Status:** In progress

Linear Regression and Random Forest Regression models will be developed and compared. The model selection procedure and results will be documented in the notebook.

### Section 5: Model Analysis

**Responsible:** Lernik Avetisyan  
**Status:** Upcoming

The selected model will be analyzed by comparing its training and testing performance, examining prediction errors and residuals, and evaluating feature importance to understand which vehicle characteristics contribute most to its predictions.

### Section 6: Conclusion and Recommendations

**Responsible:** Tejasvika Mukundh  
**Status:** Upcoming

The final section will summarize the statistical analysis, interpret the findings, discuss limitations, and provide recommendations supported by the results.

**Team collaboration:** Both team members are expected to review each other's work and contribute to the development and verification of the final project.

## 5. Predictive Models

The project will investigate two regression approaches.

**Linear Regression**

Linear Regression will be used to establish a baseline model and examine linear relationships between selected vehicle characteristics and MPG.

**Random Forest Regression**

Random Forest Regression will be used to investigate nonlinear relationships and interactions between predictors.

The models will be compared after the modeling and evaluation stages are complete. No model is assumed to perform better in advance.

## 6. Model Evaluation

The planned model evaluation will consider the following regression metrics:

- **Mean Absolute Error (MAE):** Measures the average absolute difference between predicted and actual MPG values.
- **Root Mean Squared Error (RMSE):** Measures prediction errors while assigning greater weight to larger errors.
- **Coefficient of Determination (R²):** Measures how much variation in MPG is explained by the model.

Both models will be evaluated using a consistent procedure to support a meaningful comparison.

Final evaluation results and conclusions will be added after the modeling sections are completed.

## 7. Repository Structure

```text
AAI_500-501/
├── notebooks/
│   └── Auto_MPG_Final_Project.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

**File descriptions:**

- `notebooks/Auto_MPG_Final_Project.ipynb` - Working Jupyter notebook containing the statistical analysis and project development.
- `README.md` - Project overview, methodology, team responsibilities, and repository documentation.
- `requirements.txt` - Python dependencies required for the project.
- `.gitignore` - Git configuration for excluding temporary and environment-specific files.

GitHub is used to organize project files, maintain version history, and support team collaboration. The repository will be updated as the project progresses.

The final technical report and recorded team presentation are separate deliverables submitted through Canvas.

## 8. Notebook Access and Setup

The project analysis is developed in Google Colab using Python and Jupyter Notebook. The working notebook is available in the `notebooks/` directory.

To run the project, open `Auto_MPG_Final_Project.ipynb` in Google Colab or Jupyter Notebook, install the required libraries listed in `requirements.txt`, and execute the notebook cells in order.

## 9. Team Members

**University of San Diego - AAI 500**

- **Lernik Avetisyan:** Responsible for Sections 1, 3, and 5.
- **Tejasvika Mukundh:** Responsible for Sections 2, 4, and 6.

Both team members are expected to participate in coding, reviewing the analysis, and preparing the final project deliverables.

## 10. References

Quinlan, R. (1993). *Auto MPG* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5859H

Additional references will be added as needed throughout the project.
