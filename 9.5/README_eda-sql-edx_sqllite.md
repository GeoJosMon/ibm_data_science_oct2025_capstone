
# 🚀 SpaceX Launch Data Scraping and Parsing


This Python notebook performs Exploratory Data Analysis (EDA) on the SpaceX launch dataset by loading the data into a local SQLite database and executing various SQL queries. The objective is to understand mission outcomes, payload masses, booster versions, and launch site activity.


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install sqlalchemy
!pip install ipython-sql
!pip install pandas
!pip install prettytables
````

| Library | Purpose |

| sqlalchemy | Provides the SQL toolkit and Object-Relational Mapper (ORM) for Python.|
| ipython-sql | Enables the use of %sql magic commands to execute SQL queries directly in the notebook. |
| pandas |	Used to read the CSV file into a DataFrame before loading it into the database. |
| sqlite3 |	Python's standard library used to create and manage the local database connection (my_data1.db) |


## 🌎 Data Source

The script uses a public SpaceX launch dataset:

| Source | Description |

| **Primary Data (Scraped)** | The official SpaceX launch history dataset, downloaded from an IBM cloud link: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DS0321EN-SkillsNetwork/labs/module_2/data/Spacex.csv|


## ⚙️ Script Functionality

The script performs the following sequence of operations:

### 1\. Data Acquisition

1. Connection: Establishes a local SQLite database connection to a file named my_data1.db.
2. Data Loading: Reads the external CSV file into a Pandas DataFrame (df).
3. SQL Table Creation: Loads the DataFrame contents into a SQL table named SPACEXTBL.
4. Cleaning: Creates a clean working table, SPACEXTABLE, by removing any records where the Date column is null.
5. Configuration: Sets the SQL magic output style to avoid known display errors: %config SqlMagic.style = '_DEPRECATED_DEFAULT'.


### 2\. Exploarative Data Analysis(SQL Tasks)

The notebook executes a series of SQL queries to answer specific analytical tasks (Tasks 1 through 10), including:

- Displaying unique Launch Sites.
- Calculating the total payload mass for specific customers (e.g., NASA CRS).
- Finding the average payload mass for specific booster versions (e.g., F9 v1.1).
- Determining the earliest successful drone ship landing date.
- Listing boosters that achieved ground pad success within a specific payload range.
- Classifying and counting total successful and failure mission outcomes.
- Listing booster versions that carried the maximum payload mass (using a subquery).
- Ranking landing outcomes within a specific date range.


### 4\. Output

The primary output of the notebook is the query results, displayed as HTML tables directly within the Jupyter environment. No final CSV file is generated in this specific code block.

-----

###  How to Run the Script

1. Open the .ipynb file in a Jupyter environment (Jupyter Lab or Jupyter Notebook).
2. Run the first cell containing the pip install commands.
3. Run the cells sequentially to load the SQL extension, connect to the database, load the data, and execute the analytical queries.


###  Notes

- The extraction logic is highly tailored to the specific HTML structure of the archived Wikipedia page, including handling common data inconsistencies like references, embedded links, and irregular rows.

- The script prints the shape of the final DataFrame and its head for verification.

###  Author
While majority of the code was written by Lakshmi Holla and Rav Ahuja, the Tasks section was writen by George Monappallil. Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

