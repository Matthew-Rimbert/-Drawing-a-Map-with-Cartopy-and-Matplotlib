# 🗺️ Drawing a Map with Cartopy and Matplotlib

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-1.3.0+-green.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4.2+-red.svg)
![Cartopy](https://img.shields.io/badge/Cartopy-0.19.0+-orange.svg)

## 📋 Purpose
This project demonstrates how to create a map using Cartopy and Matplotlib to show city locations in any given state.

## 🛠️ Scope
- Load data into pandas DataFrame
- Filter data for a specific geographical region
- Visualize the data on a map using Cartopy and Matplotlib

## 🚀 Installation
1. **Clone the repository:**
    ```bash
    git clone https://github.com/Matthew-Rimbert/Drawing-a-Map.git
    ```
2. **Navigate to the project directory:**
    ```bash
    cd Drawing-a-Map
    ```
3. **Install required Python packages:**
    ```bash
    pip install pandas matplotlib cartopy
    ```

## ▶️ Usage
1. **Run the script:**
    ```bash
    python drawing_map.py
    ```

2. **View the map output**.

## 🧩 Code Snippets

### Loading and Filtering Data:
The dataset of US cities is loaded, and the data is filtered to include only the cities in New Mexico. This step ensures that the map focuses on the relevant geographical region.
```python
import pandas as pd

# Load the dataset
us_cities = pd.read_csv("https://raw.githubusercontent.com/plotly/datasets/master/us-cities-top-1k.csv")

# Filter for New Mexico cities
new_mexico_cities = us_cities[us_cities.State == 'New Mexico']
```
## Visualizing the Data on a Map:
The filtered data is plotted on a map using Cartopy and Matplotlib. The map includes coastlines and formatted ticks for better readability. Each city is marked with a red dot, and city names are labeled for easy identification.
```python
import matplotlib.pyplot as plt
import cartopy.crs as ccrs
from cartopy.mpl.ticker import LongitudeFormatter, LatitudeFormatter

# Set up the map projection
fig, ax = plt.subplots(figsize=(15, 8))
ax = plt.axes(projection=ccrs.Mercator())

# Plot coastlines and set ticks
ax.coastlines('10m')
ax.set_yticks([31, 32, 33, 34, 35, 36, 37], crs=ccrs.PlateCarree())
ax.set_xticks([-109, -108, -107, -106, -105, -104], crs=ccrs.PlateCarree())

# Format the ticks
lon_formatter = LongitudeFormatter()
lat_formatter = LatitudeFormatter()
ax.xaxis.set_major_formatter(lon_formatter)
ax.yaxis.set_major_formatter(lat_formatter)

# Set the extent to focus on New Mexico
ax.set_extent([-109, -103, 31, 37])

# Extract longitude and latitude for the cities
X = new_mexico_cities['lon']
Y = new_mexico_cities['lat']
cities = new_mexico_cities['City']

# Plot the cities on the map
ax.scatter(X, Y, color='red', marker='o', transform=ccrs.PlateCarree())

# Add city names as labels
for i in X.index:
    label = cities[i]
    plt.text(X[i], Y[i] + 0.05, label, clip_on=True, fontsize=10, horizontalalignment='center', transform=ccrs.Geodetic())

plt.title('Cities in New Mexico')
plt.show()
```
## 🏙️ Example Output
![cities_of_NM](https://github.com/user-attachments/assets/1b893908-277e-4c62-a576-7f8e53ecc4be)


### Smmary
This project provides a visualization of city locations in New Mexico using Cartopy and Matplotlib. The map shows the geographic distribution of cities and provides a clear visual representation of their locations. This project showcases the capability of combining Cartopy and Matplotlib to create detailed geographical visualizations, which can be useful for various applications such as urban planning, logistics, and educational purposes.

## 🌟 Encourage Experimentation
Feel free to modify the code to visualize cities in your own state or hometown! Simply change the filtering criteria in the new_mexico_cities DataFrame to match the state or city you are interested in. This practice will help you understand how to work with geographical data and customize visualizations according to your needs.

## Build upon this...
Ideally, I would like to include additional features such as:
- # Automated Data Retrieval:
   Use APIs to fetch real-time data. For example, use a weather API to show current weather conditions in each city.
- # Advanced Data Analysis:
  To include additional data analysis, such as demographic information, economic data, or crime rates for each city.
- # Interactive Features:
  Add interactive libraries such as Folium to create an interactive map where users can zoom in/out and click on city markers for more information.

