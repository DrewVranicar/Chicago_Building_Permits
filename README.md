[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/DGX3Ghs2)
CS424 - Visualization & Visual Analytics
Drew Vranicar
Chicago Building Permits (2020-2025)


Overview:

This project explores patterns in Chicago building permits between 2020–2025 using interactive visualizations built with Vega-Lite. By engineering meaningful feature embeddings and applying PCA for dimensionality reduction, the project creates an interactive embedding explorer that enables users to investigate clusters, trends, and relationships across time, location, and permit types.

Dataset Description:

The dataset includes information on building permits issued in Chicago from 2020 through 2025. Each record includes metadata such as:
RECORD_ID: Unique permit ID
ISSUE_DATE: Date permit was issued
PERMIT_TYPE: Category of the permit (e.g., Renovation, Express Permit)
WORK_TYPE: Specific type of work (e.g., Electrical, Masonry)
REPORTED_COST: Estimated project cost
COMMUNITY_AREA_NAME: Neighborhood name
LATITUDE / LONGITUDE: Geographic coordinates


Embedding Construction:

To represent each permit as a numeric feature vector, the following was convereted:
Categorical Variables converted using the method of One Hot Encoding:
PERMIT_TYPE, WORK_TYPE, COMMUNITY_AREA_NAME


Numeric Features:

REPORTED_COST was log transformed and normalized to reduce skew
YEAR was treated as a standard numeric value

Final Embedding:
Each record was converted into a high-dimensional vector capturing permit type, work type, location, cost, and year.

Dimensionality Reduction:
To visualize the embeddings, I applied PCA to the data. I used PCA because it is fast and efficient, it preserves global variance in the data, it produces a stable and consistent layout across runs, and it enables meaningful linking back to original features/columns.
Other methods were kept in mind however PCA was sufficient enough to structure the data.


Visualization Interface:

Embedding ScatterPlot: Displays 2D projection of embeddings. Brushing allows selection of clusters or outliers.
Bar Plot: Displays count of permits by PERMIT_TYPE for the selected region in the scatterplot.
Cost Histogram: Displays distribution of REPORTED_COST for selected permit types and regions.
Line Graph: Displays timeline of permits over time.
Spatial Map: Displays selected permits in certain COMMUNITY_AREA_NAME.


Key Findings and Insights:

Clustering by Permit Type: Distinct clusters form based on PERMIT_TYPE, especially Express Permits vs. Renovations.
Cost Outliers: Several permits in the Loop had significantly higher reported costs, identifiable via the cost histogram.
Neighborhood Patterns: Some community areas consistently show higher activity, visible in spatial and bar views.



How to Run Locally:

# Start a local server in your project folder:
python -m http.server

# Then visit:
http://localhost:8000

Ensure the following files are in the same directory:
index.html
script.js
style.css
embeddings_2d_pca_sample.csv
ChicagoNeighborhoods.geojson


Key Interactions:

Brush selection in the scatterplot filters the bar chart and histogram.
Click on a permit type in the bar chart to highlight it across views.
Combined filtering allows deep dive into clusters by type, location, and cost.

LIVE DEMO:
https://uic-cs424.github.io/BuildingPermitsVisualization/




Images
Entire Visualization page:
<img width="868" height="886" alt="image" src="https://github.com/user-attachments/assets/db1a43dd-6e55-43c6-a093-92f25b37d63c" />


Using brush on Scatterplot to filter bar plot:
<img width="1576" height="721" alt="image" src="https://github.com/user-attachments/assets/bdbbd576-1341-4c3c-afdc-64165beb87b7" />














