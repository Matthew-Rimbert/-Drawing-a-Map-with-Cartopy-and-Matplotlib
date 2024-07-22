import pandas as pd
import matplotlib.pyplot as plt
import cartopy.crs as ccrs
from cartopy.mpl.ticker import LongitudeFormatter, LatitudeFormatter

# Load the dataset
us_cities = pd.read_csv("https://raw.githubusercontent.com/plotly/datasets/master/us-cities-top-1k.csv")

# Filter for Kentucky cities
kentucky_cities = us_cities[us_cities.State == 'Kentucky']

# Set up the map projection
fig, ax = plt.subplots(figsize=(15, 8))
ax = plt.axes(projection=ccrs.Mercator())

# Plot coastlines and set ticks
ax.coastlines('10m')
ax.set_yticks([36, 37, 38, 39, 40], crs=ccrs.PlateCarree())
ax.set_xticks([-89, -88, -87, -86, -85, -84], crs=ccrs.PlateCarree())

# Format the ticks
lon_formatter = LongitudeFormatter()
lat_formatter = LatitudeFormatter()
ax.xaxis.set_major_formatter(lon_formatter)
ax.yaxis.set_major_formatter(lat_formatter)

# Set the extent to focus on Kentucky
ax.set_extent([-89, -81, 36, 39])

# Extract longitude and latitude for the cities
X = kentucky_cities['lon']
Y = kentucky_cities['lat']
cities = kentucky_cities['City']

# Plot the cities on the map
ax.scatter(X, Y, color='red', marker='o', transform=ccrs.PlateCarree())

# Add city names as labels
for i in X.index:
    label = cities[i]
    plt.text(X[i], Y[i] + 0.05, label, clip_on=True, fontsize=10, horizontalalignment='center', transform=ccrs.Geodetic())

plt.title('Cities in Kentucky')
plt.show()
