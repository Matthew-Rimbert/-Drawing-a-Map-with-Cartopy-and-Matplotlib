# 🗺️ Drawing a Map with Cartopy and Matplotlib

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-1.3.0+-green.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4.2+-red.svg)
![Cartopy](https://img.shields.io/badge/Cartopy-0.19.0+-orange.svg)

## 📋 Purpose
This project demonstrates how to create a map using Cartopy and Matplotlib to show city locations in New Mexico.

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

### Loading and Filtering Data
```python
import pandas as pd

# Load the dataset
us_cities = pd.read_csv("https://raw.githubusercontent.com/plotly/datasets/master/us-cities-top-1k.csv")

# Filter for New Mexico cities
new_mexico_cities = us_cities[us_cities.State == 'New Mexico']
