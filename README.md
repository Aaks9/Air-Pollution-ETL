# 🌫️ Multi-City Air Pollution ETL & Time-Series Analysis

**Using OpenWeather Historical Air Pollution API**

---

## 📌 Project Overview

Air pollution varies significantly across cities and over time, making historical analysis essential for understanding environmental patterns.
This project builds an **end-to-end ETL (Extract, Transform, Load) pipeline** to collect, process, and analyze **historical air pollution data** for multiple major cities using the **OpenWeather Air Pollution Historical API**.

The pipeline ingests raw API data, transforms nested JSON responses into a structured time-series dataset, and performs exploratory analysis to compare pollution trends across cities.

---

## 🌍 Cities Covered

The analysis includes the following cities:

* Delhi
* Mumbai
* Bangalore
* Kolkata
* Beijing

Each city is identified using latitude and longitude coordinates, making the pipeline easily extensible to additional locations.

---

## ⏱️ Time Range

* **Last 7 days (historical data)**
* Multiple measurements per day
* Time-series granularity based on API response frequency

Each row in the final dataset represents:

> **Air pollution measurements for one city at one specific timestamp**

---

## 🔁 ETL Pipeline Design

### 🟢 Extract

* Data sourced from the **OpenWeather Air Pollution Historical API**
* Parameterized API requests using:

  * Latitude & longitude
  * Start and end Unix timestamps
* Historical endpoint used to retrieve multiple time snapshots per city

### 🟡 Transform

* Flattened nested JSON responses into a tabular structure
* Normalized Unix timestamps into readable datetime format
* Ensured schema consistency across cities and timestamps
* Built a time-series dataset with one row per city per timestamp

### 🔵 Load

* Stored processed data as a CSV file
* Implemented safe re-runnability by:

  * Appending new records
  * Deduplicating using `(city, datetime)` as unique keys

---

## 📊 Dataset Schema

| Column   | Description                      |
| -------- | -------------------------------- |
| city     | City name                        |
| lat      | Latitude                         |
| lon      | Longitude                        |
| datetime | Measurement timestamp (UTC)      |
| aqi      | Air Quality Index                |
| pm2_5    | Fine particulate matter (PM2.5)  |
| pm10     | Coarse particulate matter (PM10) |
| no2      | Nitrogen dioxide                 |
| so2      | Sulfur dioxide                   |
| o3       | Ozone                            |
| co       | Carbon monoxide                  |

---

## 📈 Analysis Performed

* Time-series visualization of PM2.5 and AQI levels
* Cross-city comparison of air quality trends
* Daily aggregation to reduce noise from high-frequency measurements
* Identification of short-term pollution fluctuations

---

## 🔍 Key Insights

* Delhi and Beijing consistently recorded higher PM2.5 and AQI levels compared to other cities.
* Pollution levels showed noticeable short-term fluctuations within the 7-day window.
* Daily aggregation significantly improved interpretability of pollution trends.
* Beijing and Delhi exhibited higher volatility in pollution metrics, suggesting greater sensitivity to environmental and urban factors.

---

## 🛠️ Tech Stack

* **Python**
* **Requests** (API integration)
* **Pandas** (data transformation & analysis)
* **Matplotlib** (visualization)
* **REST APIs**
* **Time-series data processing**
---

## 📎 Data Source

* [OpenWeather Air Pollution API](https://openweathermap.org/api/air-pollution)

---
