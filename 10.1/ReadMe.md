
# 🚀 SpaceX Launch Data: Interactive Visual Analytics with Folium

This Python notebook performs interactive visual analytics on SpaceX launch data using the Folium mapping library. The objective is to analyze the geographical location of launch sites, visualize success/failure rates, and calculate proximities to critical infrastructure (railways, highways, coastlines, and cities).


## 💻 Prerequisites

This script requires a Python environment with the following libraries installed.

```bash
!pip install folium
!pip install pandas
!pip install requests
````

| Library | Purpose |

| **requests** | Used for making HTTP requests to the SpaceX REST API. |
| **pandas** | Used for data manipulation, cleaning, and constructing the final DataFrame. |
| **folium** | Used to create interactive maps, add markers, draw lines, and visualize geospatial data. |
| **math** | Python's standard library used for calculating distances (Haversine formula). |


## 🌎 Data Source

The script uses an augmented SpaceX launch dataset that includes latitude and longitude data:

| Source | Description |

| spacex_launch_geo.csv | An augmented dataset containing SpaceX launch history with specific geographical coordinates for each launch site. Downloaded from: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DS0321EN-SkillsNetwork/datasets/spacex_launch_geo.csv |


## ⚙️ Script Functionality

The script performs the following sequence of operations to achieve the analysis objectives::

### 1\. Data Acquisition and Setup

1.  **Data Loading:** Fetches the spacex_launch_geo.csv file using requests and loads it into a Pandas DataFrame.
2.  **Map Initialization:** Creates a base Folium map centered on the USA (specifically targeting the area around NASA Johnson Space Center initially, then zoomed out to
                            view all sites).

### 2\. Interactive Visualizations (Tasks 1 & 2))

The script executes specific tasks to visualize geospatial patterns:
**Task 1: Mark Launch Sites**
    - Iterates through the dataframe to identify unique launch sites.
    - Adds folium.Circle (to highlight the area) and folium.Marker (with labels) for every launch site (e.g., KSC LC-39A, VAFB SLC-4E).

**Task 2: Visualize Launch Outcomes**
    - Classifies launches as successful (Green) or failed (Red).
    - Uses MarkerCluster to group launch records. This prevents map clutter by grouping markers when zoomed out and expanding them when zoomed in.


### 3\. Proximity Analsys (Task 3)
This section focuses on calculating and visualizing distances to key geographical features:
    **Mouse Position**: Adds a MousePosition plugin to the map, allowing the user to easily read the Lat/Long of any point on the map by hovering over it.
    **Distance Calculation**: Implements the Haversine formula to calculate the spherical distance between two geographical points
    **Infrastructure Mapping**: Draws folium.PolyLine objects connecting launch sites to the nearest:
        - Coastline (Safety)
        - Railways (Logistics)
        - Highways (Transport)
        - Cities (Safety Buffers)
    **Distance Markers**: Adds markers to the map displaying the exact distance in Kilometers on these lines.


### 4\. Output

The primary output of the notebook is an interactive HTML map generated directly within the Jupyter environment.
**Key Visual Insights Generated**
    **Launch Site Locations**: Visual confirmation that sites are located near the equator (for physics advantages) and on coastlines (for safety).
    **Success Rates**: Color-coded clusters allow for quick visual assessment of which sites have higher success rates.
    **Logistics & Safety**: Visual lines proving that launch sites are strategically placed close to railways/highways for transport but maintain a safety buffer distance 
    from populated cities.

-----

###  How to Run the Script

1. Open the .ipynb file in a Jupyter environment (Jupyter Lab, Jupyter Notebook, or VS Code).
2. Run the first cell containing the library imports and installation commands.
3. Run the cells sequentially to load data, initialize the map, and perform Tasks 1, 2, and 3.
4. Interact with the final map by zooming in/out and clicking on clusters to see individual launch outcomes.


###  Notes
Distance Logic: The distance calculation uses the Haversine formula, which accounts for the curvature of the Earth.

Performance: The map uses MarkerCluster objects to handle the large number of launch records efficiently without lagging the browser.

###  Author
George Monappallil / Adapted from IBM/Coursera Data Science Professional Certificate – Applied Data Science CapstoneLicenseThis project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

###  License
This project is shared for educational purposes. SpaceX API data is publicly available under SpaceX's terms.

