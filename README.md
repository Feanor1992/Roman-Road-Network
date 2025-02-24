# Roman-Road-Network

## Project Overview ##

This project is dedicated to creating an interactive map that visualizes the infrastructure of the ancient Roman Empire, with a particular focus on the Roman road network, ancient ports, and key cities. The primary goal is to provide users with a powerful tool to explore and analyze historical data, allowing them to study the spatial distribution of roads, ports, and cities and obtain detailed information through interactive popups.

## Data Sources ##
1. [**Roman Roads Data**](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/TI0KAU)

The dataset represents a digital version of the Roman roads, derived from the Barrington Atlas. It includes attributes such as the road type (major and minor roads), the length of the road, the data source, and a reliability measure, along with geographic information stored in shapefile format.

2. [**Ancient Ports Data**](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/3KQFUT)

The ancient ports data is based on the work of Arthur de Graauw, who compiled and geolocated ancient harbours and ports by reviewing historical documentation. The dataset comprises approximately 2,900 ancient ports and includes information like port names and their geographic coordinates. In this project, only ports located within the territory of the Roman Empire are displayed.

3. **Roman Cities Data**

The project uses a curated list of 40 key cities from the Roman Empire. For each city, the dataset provides:
- The ancient name of the city
- The province in which the city was located
- The founding date (or an approximate date)
- An estimated population figure
- The modern name (if available)

This information is used to generate detailed popups when users hover over a city marker.

## Project Components ##
1. **Data Preprocessing and Geometry Simplification**

To optimize the map’s performance, the Roman roads geometries are simplified. This is achieved by:
- Reprojecting the data into a metric coordinate system (`EPSG:3857`) so that a simplification tolerance (set, for example, to 1000 meters) can be applied.
- Simplifying the geometries using this tolerance.
- Converting the geometries back to the standard WGS84 coordinate system (`EPSG:4326`) for mapping.

2. **Interactive Map Visualization with Plotly**
The project integrates multiple layers into a single interactive map using `Plotly`. Each layer includes:
- ***Roman Roads:*** Displayed as aggregated line traces with different styling (e.g., `dodgerblue` for major roads and `silver` for minor roads). Detailed hover popups show the road type, rounded length, and data source.
- ***Ancient Ports:*** Represented by small yellow dots. When a user hovers over a port, the port name is displayed.
- ***Roman Cities:*** Displayed as red markers. Hovering over a city marker reveals its ancient name, province, founding date, population, and modern name with a red background for the popup.

3. **Interactive Dashboard with Dash**

The dashboard is built using the Dash framework, allowing users to interact with the data through:
- A dropdown menu to filter roads by class (e.g., major or minor roads).
- A map component that dynamically updates based on the selected road classes.
- Integrated static layers for cities and ports that remain visible regardless of the road filter.
- The interface is designed to update in real time as the user interacts with the dropdown, providing a seamless and engaging experience.

## Technical Implementation ##
- **Programming Language:** Python
- **Libraries and Tools:**
    - ***GeoPandas:*** For working with geospatial data, loading and transforming shapefiles.
    - ***Plotly:*** For creating interactive maps and visualizations.
    - ***Dash:*** For building the interactive web dashboard that allows user filtering and dynamic updates.
    - ***Pandas:*** For managing and processing tabular data for cities and ports.
    - ***Zipfile & OS:*** For extracting the data from zip archives and managing file paths.
- **Core Functionalities:**
    - Data extraction, loading, and preprocessing.
    - Geometry simplification to improve rendering performance.
    - Integration of multiple data layers (roads, ports, and cities) into a single map.
    - Dynamic filtering of roads via an interactive dashboard.
    - Detailed popup information for roads, cities, and ports, enabling users to get historical context at a glance.
