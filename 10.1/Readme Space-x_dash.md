
# 🚀 SpaceX Launch Records Dashboard: Interactive Visual Analytics with Dash


This Python script creates an interactive dashboard using the Plotly Dash library to analyze SpaceX launch data. The objective is to provide a user-friendly interface for exploring launch outcomes, visualizing success rates across different launch sites, and investigating correlations between payload mass and mission success.


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install pandas
!pip install dash
!pip install plotly
````

| Library | Purpose |

| pandas |	Used to read the CSV file into a DataFrame before loading it into the database. |
| dash |	The core framework for building the analytical web application (includes html, dcc, and dependencies). |
| plotly.express | Used to generate the interactive Pie and Scatter charts. |


## 🌎 Data Source

The script uses a SpaceX launch dataset stored in a CSV file:

| Source | Description |

| **spacex_launch_dash.csv** | A dataset containing SpaceX launch records, including Payload Mass, Booster Version, Launch Site, and Class (Success/Failure).|


## ⚙️ Script Functionality

The script sets up a Dash application layout and defines callback functions to achieve the following interactive tasks:

### 1\. Data setup and app installation

Data Loading: Reads spacex_launch_dash.csv into a Pandas DataFrame.
App Structure: Initializes a dash.Dash app and defines the root html.Div layout.

### 2\. Interactive Visualizations (Tasks 1 - 4)

The dashboard integrates four key components:

Task 1: Launch Site Drop-down Input success/failure clustering.
- Implements a dcc.Dropdown component allowing users to select a specific launch site (e.g., KSC LC-39A, CCAFS SLC-40) or "All Sites".

Task 2: Launch Success Pie Chart
- Visualization: A dynamic dcc.Graph (Pie Chart).
- Logic (Callback):
  - If "All Sites" is selected: Shows the total count of successful launches, broken down by launch site.
  - If a specific site is selected: Shows the ratio of Successful (Class=1) vs. Failed (Class=0) launches for that specific site.

Task 3: Payload Range Slider
- Implements a dcc.RangeSlider to filter data by Payload Mass (Kg).
- Range: 0 Kg to 10,000 Kg, with steps of 1,000 Kg.

Task 4: Payload vs. Success Scatter Chart
- Visualization: A dynamic dcc.Graph (Scatter Plot).
- Logic (Callback):
  - Filters the dataset based on the selected Payload Range (from Task 3).
  - Plots Payload Mass (Kg) on the x-axis vs. Class (Outcome) on the y-axis.
  - Color Encoding: Uses Booster Version Category to color-code the scatter points, revealing patterns in booster reliability.


### 3\. Output

The primary output is a local web server hosting the interactive dashboard.

Key Visual Insights Generated

- Site Performance: Quickly identify which launch sites have the highest success rates.
- Payload Correlation: Observe if heavier payloads are more likely to fail or succeed.
- Booster Reliability: Visually compare the success outcomes of different Booster Versions (e.g., v1.1, FT, B4, B5) across different payload weights.

-----

###  How to Run the Script

1. Ensure spacex_launch_dash.csv is in the same directory as the script.
2. Open the .py file in your Python IDE or terminal.
3. Run the script: python spacex_dash_app.py (or the name of your file).
4. Open the local server URL provided in the terminal (usually http://127.0.0.1:8050/) in your web browser to interact with the dashboard.

### Notes

Callbacks: The dashboard relies on Dash @app.callback decorators to link inputs (Dropdown, Slider) to outputs (Charts) in real-time.

Interactivity: Changes to the Dropdown or Slider instantly trigger a re-render of the relevant graphs.

###  Author
George Monappallil. Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

