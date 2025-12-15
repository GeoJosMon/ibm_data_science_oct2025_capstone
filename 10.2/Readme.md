
# 🚀 SpaceX Launch Launch Prediction: Machine Learning Comparative Analysis

This Python notebook performs predictive analysis on SpaceX launch data using the Scikit-Learn library. The objective is to train and compare four different machine learning classification algorithms (Logistic Regression, SVM, Decision Tree, and K-Nearest Neighbors) to predict the success of a rocket landing.


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

!pip install pandas
!pip install numpy
!pip install scikit-learn
!pip install seaborn
!pip install matplotlib

| Library | Purpose |

| pandas |	Used to read the CSV file into a DataFrame before loading it into the database. |
| numpy |	Used for high-level mathematical functions and array manipulations. |
| scikit-learn | The core library used for data splitting, preprocessing (StandardScaler), model training, and hyperparameter tuning (GridSearchCV). |
| seaborn | Used to plot the confusion matrices and the final model comparison bar chart. |
| matplotlib| Used for creating the visualization framework. |


## 🌎 Data Source

The script uses a SpaceX launch dataset stored in a CSV file:

| Source | Description |

| **dataset_part_2.csv** | Contains the class labels (0 for Failure, 1 for Success) used as the target variable (Y).|
| **dataset_part_3.csv** | Contains the One-Hot Encoded feature set (FlightNumber, PayloadMass, Orbit types, etc.) used as input (X).|


## ⚙️ Script Functionality

The script sets up a Dash application layout and defines callback functions to achieve the following interactive tasks:

### 1\. Data Acquisition and Preprocessing (Tasks 1 - 3)

1. Data Loading: Fetches the datasets using requests or pandas and converts the Class column into a NumPy array.
2. Standardization: Applies StandardScaler to the feature set (X) to ensure all variables have a mean of 0 and standard deviation of 1.
3. Train/Test Split: Uses train_test_split to divide the data into Training (80%) and Testing (20%) sets.


### 2\. Model Training & Tuning (Tasks 4 - 11)

The script trains four different classification models. For each model, GridSearchCV is used to find the best hyperparameters (e.g., regularization strength, kernel type, tree depth).

**Model 1: Logistic Regression**
- Optimizes parameters: C (regularization strength), penalty, and solver.
- Calculates accuracy and visualizes the Confusion Matrix.

**Model 2: Support Vector Machine (SVM)**
- Optimizes parameters: kernel (linear, rbf, sigmoid), C, and gamma.
- Calculates accuracy and visualizes the Confusion Matrix.

**Model 3: Decision Tree Classifier**
- Optimizes parameters: criterion, max_depth, min_samples_split.
- Calculates accuracy and visualizes the Confusion Matrix.

**Model 4: K-Nearest Neighbors (KNN)**
- Optimizes parameters: n_neighbors (number of neighbors), algorithm, and p (distance metric).
- Calculates accuracy and visualizes the Confusion Matrix.


### 3\. Output

The primary output of the notebook is a comparative analysis of the models.

Key Visual Insights Generated
- Confusion Matrices: Visual heatmaps for every model showing True Positives, False Positives, True Negatives, and False Negatives.
- Accuracy Comparison: A final Bar Chart comparing the test set accuracy of all four models to identify the best performer.

-----

###  How to Run the Script

1. Open the .ipynb file in a Jupyter environment (Jupyter Lab, Jupyter Notebook, or VS Code).
2. Run the first cell containing the library imports and installation commands.
3. Run the cells sequentially to load data, preprocess features, and train the models.
4. View the final output cell to see the Model Accuracy Comparison bar chart.

### Notes

Performance: All models often converge on a similar accuracy score (approx. 83.33%) due to the dataset size. Methodology: The use of GridSearchCV with cv=10 (10-fold cross-validation) ensures that the selected hyperparameters are robust and not biased by a single train/test split.

###  Author
George Monappallil. Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

