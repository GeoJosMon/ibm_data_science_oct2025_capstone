
# 🚀 SpaceX Launch Data Scraping and Parsing

This Python script is designed to perform web scraping on a specific Wikipedia article to extract historical SpaceX launch data and structure it into a clean Pandas DataFrame. The script uses BeautifulSoup for HTML parsing and regular expressions for robust data extraction.

The final output is spacex_web_scraped.csv—a curated dataset containing launch records parsed directly from the web tables.


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

The script extracts data from the HTML tables of a specific archived version of the Wikipedia page listing Falcon 9 and Falcon Heavy launches:

| Source | Description |

| **Primary Data (Scraped)** | HTML content from the Wikipedia article: https://en.wikipedia.org/w/index.php?title=List_of_Falcon_9_and_Falcon_Heavy_launches&oldid=1027686922 |



## ⚙️ Script Functionality

The script performs the following sequence of operations:

### 1\. Data Acquisition (API Calls)

1. Request: Fetches the HTML content of the target Wikipedia URL using requests.get() with a defined User-Agent header.

2. Parsing: Creates a BeautifulSoup object (soup) from the HTML response text for structured searching.

3. Table Identification: Locates all <table> elements and selects the main launch table (assumed to be html_tables[2]).:


### 2\. Data Enrichment (Helper Functions)

The script uses helper functions to clean and extract data from individual table cells:

extract_column_from_header(row): Cleans <th> tags by removing extraneous tags (<br>, <a>, <sup>) to extract reliable column names.

- get_Date_Time(table_cells): Extracts Date and Time from a cell, using regex for pattern matching to ignore references and noise.

- get_Booster_Version(table_cells): Extracts the Booster Version string from a cell.

- get_Landing_Status(table_cells): Extracts the landing status string.

- get_Mass(table_cells): Extracts the Payload Mass, handling Unicode characters and stripping the "kg" unit.


### 3\. Data Parsing and Structuring

1. Header Extraction: Iterates through the main table's headers (<th>) to generate a list of clean column_names.

2. Dictionary Initialization: Initializes the launch_dict dictionary with these column names, setting the values to empty lists. An irrelevant column (Date and time ( )) is removed.

3. Row Iteration: Iterates through every row (<tr>) of the main data tables:

    - It uses the <th> content to identify the Flight Number (must be a digit) to determine if the row is a valid launch record.

    - It includes robust checks to skip rows that are headers, empty of <td> cells, or have insufficient columns, preventing IndexError.

    - For valid rows, it applies the helper functions to extract 11 features (Flight No., Date, Time, Version Booster, etc.) and appends   them to the corresponding lists in launch_dict.
  
4. DataFrame Creation: Converts the populated launch_dict into a Pandas DataFrame (df).


### 4\. Output

The final structured dataset is stored in the DataFrame df and exported to a CSV file named spacex_web_scraped.csv.

-----

###  How to Run the Script

1.  Save the entire code block as a Python file (e.g., spacex_web_scraper.py)..
2.  Ensure you have an active internet connection to access the Wikipedia URL.
3.  Execute the script:
    ```bash
    python spacex_data_wrangling.py
    ```
4.  The final output file, `spacex_web_scraped.csv`, will be created in the same directory.


###  Notes

- The extraction logic is highly tailored to the specific HTML structure of the archived Wikipedia page, including handling common data inconsistencies like references, embedded links, and irregular rows.

- The script prints the shape of the final DataFrame and its head for verification.


###  Author
George Monappallil / Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

