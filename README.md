# 🚲 London Bike Sharing Data Analytics Project

An end-to-end **Data Analytics Project** that analyzes the **London Bike Sharing Dataset** using **Python** and **Tableau**. The project demonstrates the complete data analytics workflow from data preprocessing to interactive dashboard development and business insight generation.

---

# 📌 Project Overview

The primary objective of this project is to analyze historical London bike-sharing data to identify commuter behavior, seasonal demand, and the impact of environmental conditions on bike rentals.

The project covers:

- Automated dataset acquisition using the Kaggle API
- Data cleaning and preprocessing with Python
- Feature engineering and categorical value mapping
- Exploratory Data Analysis (EDA)
- Interactive dashboard creation in Tableau/Power BI
- Business insight generation

---

# 📂 Dataset

**Dataset:** London Bike Sharing Dataset

The dataset contains hourly records of London's bike-sharing system along with weather and seasonal information.

### Dataset Features

| Column | Description |
|---------|-------------|
| timestamp | Date and time of observation |
| cnt | Number of bike rentals |
| t1 | Actual temperature (°C) |
| t2 | Feels-like temperature (°C) |
| hum | Humidity (%) |
| wind_speed | Wind speed (km/h) |
| weather_code | Weather condition code |
| is_holiday | Holiday indicator |
| is_weekend | Weekend indicator |
| season | Season code |

---

# 🛠️ Tools & Technologies

| Technology | Purpose |
|------------|----------|
| Python | Data preprocessing |
| Pandas | Data manipulation |
| NumPy | Numerical analysis |
| Kaggle API | Dataset download |
| Zipfile | Archive extraction |
| OS | File management |
| Openpyxl | Excel export |
| Tableau | Interactive dashboard |
| Power BI | Business Intelligence dashboard |
| Jupyter Notebook | Data analysis environment |

---

# 🔄 Project Workflow

## 1. Data Ingestion

The dataset was automatically downloaded from Kaggle using the Kaggle API.

```python
import os
import zipfile

os.system("kaggle datasets download -d hmavrodiev/london-bike-sharing-dataset")

with zipfile.ZipFile("london-bike-sharing-dataset.zip","r") as zip_ref:
    zip_ref.extractall()
```

---

## 2. Data Inspection

Performed:

- Shape verification
- Data type inspection
- Missing value analysis
- Statistical summary
- Unique value analysis

```python
bikes.info()

bikes.describe()

bikes.isnull().sum()
```

Dataset Size

- **Rows:** 17,414
- **Columns:** 10

---

## 3. Data Cleaning

Renamed columns for improved readability.

```python
new_cols_dict = {

'timestamp':'time',

'cnt':'count',

't1':'temp_real_C',

't2':'temp_feels_like_C',

'hum':'humidity_percent',

'wind_speed':'wind_speed_kph',

'weather_code':'weather',

'is_holiday':'is_holiday',

'is_weekend':'is_weekend',

'season':'season'

}

bikes.rename(columns=new_cols_dict,inplace=True)
```

---

## 4. Feature Engineering

### Humidity Conversion

Converted humidity values into decimal fractions.

```python
bikes['humidity_percent'] = bikes['humidity_percent'] / 100
```

### Season Mapping

```python
season_dict = {

'0.0':'Spring',

'1.0':'Summer',

'2.0':'Autumn',

'3.0':'Winter'

}

bikes['season'] = bikes['season'].astype(str).map(season_dict)
```

### Weather Mapping

```python
weather_dict = {

'1.0':'Clear',

'2.0':'Scattered Clouds',

'3.0':'Broken Clouds',

'4.0':'Cloudy',

'7.0':'Rain',

'10.0':'Rain with Thunderstorm',

'26.0':'Snowfall'

}

bikes['weather'] = bikes['weather'].astype(str).map(weather_dict)
```

---

## 5. Export Processed Dataset

```python
bikes.to_excel("london_bikes_final.xlsx",index=False)
```

The cleaned dataset was exported for visualization in Tableau and Power BI.

---

# 📊 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Bike rental trends over time
- Hourly demand distribution
- Seasonal comparison
- Weather impact analysis
- Temperature relationship
- Weekend vs Weekday usage
- Holiday effect
- Humidity analysis

Visualization libraries:

```python
import matplotlib.pyplot as plt
import seaborn as sns
```

Example:

```python
sns.histplot(bikes['count'])

plt.show()
```

---

# 📈 Tableau / Power BI Dashboard

The processed dataset was imported into Tableau/Power BI to build an interactive dashboard.

## Dashboard Components

- KPI Cards
- Daily Bike Rentals
- Monthly Trend
- Moving Average Chart
- Hourly Heatmap
- Weather Analysis
- Seasonal Comparison
- Weekend vs Weekday Analysis
- Interactive Filters

---

# 📊 Dashboard Insights

### 🚲 Peak Riding Hours

- Morning commute around **08:00**
- Evening commute around **17:00**

---

### ☀️ Weather Impact

Highest rentals during:

- Clear
- Scattered Clouds

Lowest rentals during:

- Rain
- Snowfall
- High Humidity

---

### 🌸 Seasonal Trends

Highest demand:

- Summer
- Spring

Lowest demand:

- Winter

---

### 📅 Weekend Behavior

Weekdays:

- Strong commuting pattern

Weekends:

- More consistent daytime usage

---

# 📈 Business Insights

## Fleet Optimization

Increase bike availability during:

- Summer
- Spring
- Rush hours

---

## Weather Planning

Use weather forecasts to:

- Predict rental demand
- Improve bike redistribution
- Optimize maintenance schedules

---

## Operational Efficiency

Deploy additional bikes:

- Business districts during weekdays
- Parks and tourist locations during weekends

---

# 📁 Folder Structure

```text
London-Bike-Sharing-Analysis/
│
├── .kaggle/
│   └── kaggle.json
│
├── data/
│   ├── london_merged.csv
│   └── london_bikes_final.xlsx
│
├── notebooks/
│   └── London Bike Rides Notebook.ipynb
│
├── dashboard/
│   ├── London Bike Rides Analysis.twb
│   └── London Bike Dashboard.pbix
│
├── reports/
│   └── Bike_Sharing_Report.pdf
│
├── images/
│   ├── dashboard.png
│   ├── heatmap.png
│   └── moving_average.png
│
└── README.md
```

---

# 📊 Project Architecture

```text
Kaggle API
     │
     ▼
Raw CSV Dataset
     │
     ▼
Python + Pandas
     │
     ▼
Data Cleaning
     │
     ▼
Feature Engineering
     │
     ▼
Exploratory Data Analysis
     │
     ▼
Excel Dataset
     │
     ▼
Tableau / Power BI
     │
     ▼
Interactive Dashboard
     │
     ▼
Business Insights
```

---

# 🚀 Future Improvements

- Demand forecasting using Machine Learning
- Time-series analysis with ARIMA or Prophet
- Real-time dashboard integration
- Predictive maintenance analytics
- Geospatial route optimization
- Weather-based rental prediction

---

# 📌 Results

- Successfully automated dataset retrieval using the Kaggle API.
- Cleaned and transformed **17,414** hourly bike-sharing records.
- Improved dataset readability through descriptive column names and categorical mapping.
- Built interactive Tableau/Power BI dashboards to visualize rental patterns.
- Identified peak commuting hours, seasonal demand, and weather impacts on bike usage.
- Generated actionable insights to support fleet optimization and operational planning.

---

