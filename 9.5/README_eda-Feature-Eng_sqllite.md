
# 🚀 SpaceX Launch Data Scraping and Parsing


This Python script performs Exploratory Data Analysis (EDA) and Feature Engineering on the curated SpaceX launch dataset (dataset_part_2.csv). The objective is to visualize relationships between key features (Flight Number, Payload Mass, Orbit, Launch Site) and the mission outcome (Class) to prepare the data for a subsequent machine learning prediction model.


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install numpy
!pip install pandas
!pip install seaborn
!pip install requests
````

| Library | Purpose |

| numpy | Used for numerical operations.|
| matplotlib.pyplot | Used for basic plotting functions like setting labels, titles, and displaying charts. |
| pandas |	Used to read the CSV file into a DataFrame before loading it into the database. |
| seaborn |	Used for creating informative statistical graphics, particularly catplot and lineplot visualizations. |
| requests & io | Used for downloading the required CSV file into memory for reading. |


## 🌎 Data Source

The script uses a public SpaceX launch dataset:

| Source | Description |

| **Primary Data (CSV)** | The pre-processed SpaceX launch data, ready for visualization and feature engineering: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DS0321EN-SkillsNetwork/datasets/dataset_part_2.csv|


## ⚙️ Script Functionality

The script performs the following sequence of operations:

### 1\. Data Acquisition

The pre-processed SpaceX launch data, ready for visualization and feature engineering: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DS0321EN-SkillsNetwork/datasets/dataset_part_2.csv
1. Request: Uses the Python requests library to fetch the CSV file content from the cloud storage URL.
2. In-Memory Handling: The content is read into a BytesIO object.
3. Data Loading: The BytesIO object is used by pd.read_csv() to create the working Pandas DataFrame (df).

### 2\. Exploarative Data Analysis(Viualization Tasks 1-6)

The core of the EDA involves creating visualizations to understand how different variables relate to the mission Class (0=Failure, 1=Success):

- Task 1 & 2: Visualize FlightNumber and PayloadMass against LaunchSite using scatter plots (sns.catplot) to observe success/failure clustering.
- Task 3: Visualize the average success rate (Class mean) for each Orbit type using a bar chart (sns.barplot).
- Task 4 & 5: Visualize FlightNumber and PayloadMass against Orbit type using scatter plots (sns.catplot).
- Task 6: Calculate and visualize the launch success yearly trend using a line chart, after extracting the year from the Date column.

### 3\. Feature Engineering(Tasks 7 & 8)

The script prepares the data for subsequent machine learning modules:

- Feature Selection: A subset of relevant features is selected into the features DataFrame.
- Task 7 (One-Hot Encoding): Categorical columns (Orbit, LaunchSite, LandingPad, Serial) are converted into numerical binary columns using pd.get_dummies() and stored in features_one_hot.
- Task 8 (Casting): The entire features_one_hot DataFrame is cast to the float64 data type to ensure numerical consistency.

### 4\. Output

The final processed feature set, features_one_hot, is exported to a new CSV file named dataset_part_3.csv.

-----

###  How to Run the Script

1. Open the .ipynb file in a Jupyter environment.
2. Run the initial cells to install libraries and import necessary modules.
3. Execute the data loading cell (pd.read_csv(...)) to load the df DataFrame.
4. Run the subsequent cells sequentially to generate visualizations and perform feature engineering.

###  Author
While majority of the code was written by Pratiksha Verma and RAnita Verma (Clarified instructions), the Tasks section was writen by George Monappallil. Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

