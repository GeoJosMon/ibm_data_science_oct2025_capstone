
# 🚀 SpaceX Falcon 9 Data Collection: Web Scraping

This Jupyter Notebook (9.4-Web-Scraper.ipynb) performs web scraping to gather historical Falcon 9 launch data from Wikipedia. The objective is to extract detailed launch records—including payload mass, customer details, and landing outcomes—to supplement data collected from the SpaceX API


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install beautifulsoup4
!pip install requests
!pip install pandas
!pip install numpy
````

| Library | Purpose |

| BeautifulSoup4 |	Used for parsing HTML content and navigating the DOM structure.|
| requests |	Used for making an HTTP GET request to fetch the Wikipedia page HTML. |
| pandas |	Used for constructing the final DataFrame and exporting data to CSV. |
| numpy |	Used for numerical operations. |
| re (regex) |	Used within helper functions (like get_Date_Time) for robust pattern matching. |
| unicodedata	| Used within helper functions (like get_Mass) for normalizing text content. |




## 🌎 Data Source

The script targets a specific version of the Wikipedia list of Falcon 9 launches to ensure data consistency:

| Source | Description |

| Wikipedia | Tables in the Wikipedia page|



## ⚙️ Script Functionality

the notebook is structured into sequential tasks to request, parse, and structure the data:

### 1\. Requesting the Data (Task 1)

1. HTTP Request: Uses requests.get() to fetch the HTML content from the static Wikipedia URL.

2. Response Check: Verifies the status code (200) to ensure the page was retrieved successfully.


### 2\. Parsing HTML Tables (Task 2)

- BeautifulSoup Object: Creates a soup object to traverse the HTML structure.
- Column Extraction: Iterates through the HTML table headers (<th>) to define the columns for the dataset (e.g., "Flight No.", "Date and time", "Payload mass").


### 3\. Data Extraction & Cleaning (Task 3)

The script iterates through the table rows (<tr>) and cells (<td>) to extract specific data points using custom helper functions:

- get_Date_Time(): Extracts and formats the launch date and time.
- get_Booster_Version(): Cleans the booster version string.
- get_Mass(): Normalizes payload mass data, removing "kg" and handling non-breaking spaces.
- get_Landing_Status(): Extracts the specific landing outcome (e.g., "Success", "Failure").


### 4\. Output

The scraped data is stored in a Python dictionary and then converted into a Pandas DataFrame.

Key Output:
spacex_web_scraped.csv: A structured CSV file containing all scraped launch records, ready for data wrangling and analysis.

-----

###  How to Run the Script

1.  Ensure you have 9.4-Web-Scraper.ipynb saved in your working directory.
2.  Open the file in Jupyter Lab, Jupyter Notebook, or VS Code.
3.  Run the cells sequentially to install dependencies and execute the scraping logic.
4.  Upon completion, the file spacex_web_scraped.csv will be created in the same directory.


###  Author
George Monappallil Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science Capstone

###  License
This project is shared for educational purposes. The data source (Wikipedia) is available under the Creative Commons Attribution-ShareAlike License.

