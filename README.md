# ibm_data_science_oct2025_capstone
**CAPSTONE PROJECT FOR IBM DATA SCIENCE OCT 2025**


***PROJECT OVERVIEW***
The commercial space industry has been revolutionized by SpaceX's introduction of the Falcon 9, a reusable rocket that significantly reduces the cost of space access. While expendable rockets cost upwards of $165 million per launch, a reused Falcon 9 drops the cost to approximately $62 million.

The main objective of this Capstone project is to predict whether the Falcon 9 first stage will land successfully. By leveraging historical launch data and machine learning algorithms, we can determine the likelihood of a successful landing, enabling competitors and stakeholders to estimate the true cost of a launch for strategic bidding.

***METHODOLOGY***
**1. Data Collection**
- SpaceX REST API: Real-time launch data was extracted using GET requests from api.spacexdata.com/v4/launches/past.
    - Features Extracted: Booster version, Payload mass, Orbit, and Launch Site.

- Web Scraping: Historical launch records were scraped from the Wikipedia page "List of Falcon 9 and Falcon Heavy launches" using BeautifulSoup to supplement API gaps.

**2. Data Wrangling & Preprocessing**
- Filtering: The dataset was filtered to include only Falcon 9 launches, removing Falcon 1 and Falcon Heavy records.
- Missing Values: Null values in PayloadMass were replaced with the mean mass for that specific class.
- Outcome Classification: A binary "Class" variable was created:

    1 = Success (True Ocean, True RTLS, True ASDS).
    0 = Failure (False Ocean, False RTLS, None, etc.).

**3. Exploratory Data Analysis (EDA)**

- SQL Analysis: Used SQL to query key performance indicators, such as identifying the first successful ground pad landing (2015-12-22) and calculating total payload masses.
- Visualization: Used Matplotlib and Seaborn to visualize trends:

    - Flight Number vs. Launch Site: Revealed that early failures were concentrated at CCAFS SLC-40, while later sites like KSC LC-39A showed high reliability.
   - Payload Mass vs. Success: Disproved the myth that heavier payloads are riskier; heavy payloads (>10,000 kg) showed a near-perfect success record.
   - Orbit Analysis: Identified that LEO and ISS missions are the program's "bread and butter," while Polar orbits emerged later with the activation of VAFB SLC-4E.

**4. Interactive Analytics**

- Folium Maps: Mapped launch sites to visualize safety buffers (coastline proximity) and logistical requirements (proximity to railways for heavy transport).
- Plotly Dash Dashboard: Created an interactive dashboard allowing users to filter by launch site and payload mass to analyze success rates dynamically.

**5. Predictive Analysis (Machine Learning)**

Four classification models were built and optimized using GridSearchCV with 10-fold cross-validation:

1. Logistic Regression
2. Support Vector Machine (SVM)
3. Decision Tree
4. K-Nearest Neighbors (KNN)


**Results:**

**Accuracy:** All four models achieved an identical test set accuracy of 83.33%.
**Best Model:** Logistic Regression was selected as the optimal model due to its computational efficiency and interpretability compared to more complex models.
**Error Analysis:** The models had high recall for successful landings (100% True Positives) but occasionally predicted success for failed missions (False Positives).

**KEY INSIGHTS**

**Reliability Growth:**
Success rates have improved significantly over time, particularly after the introduction of the "Full Thrust" (FT) booster version.
**Site Specialization:** KSC LC-39A handles the majority of heavy-lift commercial missions, while VAFB SLC-4E is specialized for Polar orbits.
**Predictability:** Rocket reusability has transitioned from an experimental phase to a predictable, data-driven operation.

***TECH STACK***
- Languages: Python, SQL
- Libraries: Pandas, NumPy, Matplotlib, Seaborn, Folium, Plotly Dash, Scikit-learn, BeautifulSoup, Requests

***AUTHOR***
George Monappallil
