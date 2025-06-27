# ✈️ Plane Crash Analysis Dashboard

This project is an end-to-end data analytics workflow focused on global plane crash data from 1918 to 2022. It uses **Python**, **MySQL**, and **Power BI** to uncover key trends and patterns and visualize them in a dynamic dashboard.

---

## 📦 Dataset Summary

**File Used**: `cleaned_plane_crashes.xlsx`  
**Total Records**: 22,696  
**Columns**: 24

### 🔑 Key Columns

| Column Name         | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `Date`, `Date1`     | Date of the crash (duplicated for backup/format reasons)                   |
| `Aircraft`          | Model and type of the aircraft involved                                     |
| `Operator`          | Company or military operator of the aircraft                                |
| `Flight phase`      | Phase during which the crash occurred (e.g., takeoff, landing)              |
| `Flight type`       | Purpose of flight (commercial, military, cargo, etc.)                        |
| `Crash site`        | Location type (e.g., airport vicinity, mountain, etc.)                      |
| `Schedule`          | Flight route (departure - arrival airports)                                 |
| `Crash location`    | Detailed crash place (village, city, etc.)                                  |
| `Country`, `Region` | Geographical information of crash site                                      |
| `Crew on board`     | Number of crew members on board                                             |
| `Crew fatalities`   | Number of crew members who died                                             |
| `Pax on board`      | Number of passengers on board                                               |
| `PAX fatalities`    | Number of passengers who died                                               |
| `Other fatalities`  | Any other individuals killed (e.g., on ground)                              |
| `Total fatalities`  | Sum of all fatalities                                                       |
| `Circumstances`     | Narrative description of the crash                                          |
| `Crash cause`       | Categorized reason (e.g., Human error, Technical failure, Weather)          |

---

## 🧹 Data Preparation (Python)

- Missing values filled using appropriate strategies (e.g., `'Unknown'` for strings, `0` for counts).
- Date columns converted to datetime format.
- Non-numeric columns like `Pax on board` cast from object to integers (after cleanup).
- Dataset exported to `.csv` and imported into MySQL.

---

## 🗃️ SQL Analysis

Stored in `/sql_queries/`:
- Crashes per year
- Top aircraft models by incidents
- Fatalities by region and cause
- Ranking most fatal crashes
- Crash cause distribution

---

## 📊 Power BI Dashboard

Connected directly to MySQL database to create visuals:
- **Time Trend**: Crashes per year
- **Map**: Crashes by country
- **Bar Charts**: Aircraft types, crash causes
- **KPI Cards**: Total crashes, total deaths, most common cause
- **Slicers**: Year, region, cause, aircraft model

---

## 🔮 Insights Discovered

- Human factors were the leading cause of crashes.
- Most crashes occurred during **landing** and **takeoff**.
- Certain decades (e.g., 1940s–1970s) had higher incidents due to wartime and early aviation development.
- Passenger fatalities are often higher in commercial aircraft compared to military or cargo.

---

## 📁 File Structure

```
├── cleaned_plane_crashes.xlsx     # Dataset used
├── python_scripts/
│   └── data_cleaning.py           # Python code for preprocessing
├── sql_queries/
│   └── plane_crash_analysis.sql   # MySQL scripts for analysis
├── dashboard/
│   └── PowerBI_Report.pbix        # Final Power BI dashboard file
└── README.md                      # Project overview (this file)
```

---

## 📌 To-Do / Enhancements

- Add Streamlit dashboard
- Perform machine learning-based crash cause classification
- Connect Power BI dashboard to live MySQL database online

---

## 🧑‍💻 Author

Utkarsh Shikhar  
Data Analyst | Python • SQL • Power BI  
📧 utkarsh.shikhar@gmail.com  
📍 Delhi, India

---
