
# 🚀 SpaceX Launch Data Processing and Wrangling

This Python script is designed to acquire historical SpaceX launch data from the SpaceX API, process the raw JSON response, enrich the dataset by making additional API calls for detailed component information (like booster and payload data), and perform initial data wrangling and cleaning to prepare a dataset suitable for analysis or machine learning tasks.
The final output is `dataset_part_1.csv` — a curated dataset containing only Falcon 9 launches up to November 13, 2020.


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install requests
!pip install pandas
!pip install numpy
````

| Library | Purpose |

| **requests** | Used for making HTTP requests to the SpaceX REST API. |
| **pandas** | Used for data manipulation, cleaning, and constructing the final DataFrame. |
| **numpy** | Used for numerical operations, including handling `np.nan` values. |
| **datetime** | Used for date filtering and conversion. |


## 🌎 Data Source

The script primarily pulls data from two locations:

| Source | Description |

| **Primary Data (Live)** | The initial list of past launches is fetched directly from the official **SpaceX REST API** endpoint: `https://api.spacexdata.com/v4/launches/past` |
| **Static Data (Enrichment)** | A static JSON file is used as a consistent reference for the primary data structure, retrieved from an IBM cloud object storage link: `https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DS0321EN-SkillsNetwork/datasets/API_call_spacex_api.json` |
Additional endpoints used:/rockets/{id}
/launchpads/{id}
/payloads/{id}
/cores/{id}


## ⚙️ Script Functionality

The script performs the following sequence of operations:

### 1\. Data Acquisition (API Calls)

1.  **Initial Request:** Fetches the list of past launches from the main endpoint (`https://api.spacexdata.com/v4/launches/past`).
2.  **Normalization:** Converts the primary JSON response into a flat Pandas DataFrame using `pd.json_normalize()`.
3.  **Data Filtering:**
      * Subsets the DataFrame to key columns: `rocket`, `payloads`, `launchpad`, `cores`, `flight_number`, and `date_utc`.
      * Filters the data to include only launches with a **single core** and a **single payload** (simplifying the dataset for Falcon 9 analysis).

### 2\. Data Enrichment (Helper Functions)

The script uses four defined helper functions to call specific SpaceX API endpoints for each launch and retrieve detailed information:

  * `getBoosterVersion(data)`: Retrieves the **Booster Version** name (e.g., 'Falcon 9').
  * `getLaunchSite(data)`: Retrieves **Launch Site** name, **Longitude**, and **Latitude**.
  * `getPayloadData(data)`: Retrieves **Payload Mass** and **Orbit**.
  * `getCoreData(data)`: Retrieves **Core Block**, **Reused Count**, **Serial**, **Outcome**, **Flights**, **Grid Fins**, **Reused**, **Legs**, and **Landing Pad** status.

These functions are designed to append data to global lists, ensuring that a placeholder value (`None`) is added if data is missing, which prevents the `ValueError: All arrays must be of the same length` error when constructing the final DataFrame.

### 3\. Data Wrangling and Cleaning

1.  **Date Conversion:** Converts the `date_utc` column to a standard date format.
2.  **Date Restriction:** Filters the dataset to include only launches that occurred **before or on November 13, 2020**.
3.  **DataFrame Construction:** Combines all collected data into a single DataFrame (`df`) using the `launch_dict`.
4.  **Falcon 9 Filtering:** Creates a new DataFrame, `data_falcon9`, by removing the 'Falcon 1' launches. The `FlightNumber` is reset to start from 1 for the new filtered dataset.
5.  **Mean Imputation:** Calculates the **mean** of the `PayloadMass` column and uses it to replace all missing (`np.nan`) values in that column.

### 4\. Output

The final cleaned and wrangled dataset, stored in the `data_falcon9` DataFrame, is exported to a CSV file named **`dataset_part_1.csv`**.

-----

###  How to Run the Script

1.  Save the entire code block as a Python file (e.g., `spacex_data_wrangling.py`).
2.  Ensure you have an active internet connection to access the SpaceX API endpoints.
3.  Execute the script:
    ```bash
    python spacex_data_wrangling.py
    ```
4.  The final output file, `dataset_part_1.csv`, will be created in the same directory.


###  Notes
The dataset is restricted to launches on or before 2020-11-13 as per the original lab requirements.
Falcon 1 launches are excluded.
Only missions with a single core and single payload are kept (standard Falcon 9 configuration).
Missing PayloadMass values are imputed using the mean of known values.

###  Author
George Monappallil / Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

