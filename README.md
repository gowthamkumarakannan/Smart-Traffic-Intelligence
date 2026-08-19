# 🚦 TrafficPulse AI

### Real-Time Traffic Monitoring, Congestion Prediction & Smart Decision Intelligence

TrafficPulse AI is an end-to-end Smart Traffic Intelligence project combining **Excel, MySQL, Python, Machine Learning, Power BI, NLP/LLM and RAG** to analyze traffic conditions, congestion, incidents, weather impact, road risk and signal performance.

## 🎯 Project Objective

TrafficPulse AI transforms raw traffic data into actionable intelligence and helps answer:

- Which roads have the highest congestion?
- Which roads are high risk?
- How do incidents affect traffic?
- How does weather influence congestion?
- Which junctions and signals need attention?
- Can traffic conditions and risk be predicted?
- Can AI generate traffic recommendations?

## 🏗️ Project Workflow

```text
01 Data Acquisition
        ↓
02 Excel Analysis
        ↓
03 MySQL Database
        ↓
04 Statistical Analysis
        ↓
05 Machine Learning
        ↓
06 Power BI Dashboard
        ↓
07 AI / LLM Analytics
        ↓
08 Executive Presentation
        ↓
09 GitHub
```

## 📊 Datasets

The project uses five raw datasets:

```text
01_Traffic_Raw.xlsx
02_Incident_Raw.xlsx
03_Weather_Raw.xlsx
04_Road_Raw.xlsx
05_Signal_Raw.xlsx
```

### Traffic Data
Traffic ID, road ID, road name, timestamp, vehicle count, average speed, road occupancy, congestion score, traffic condition, risk level and incident information.

### Incident Data
Incident ID, road ID, incident type, incident severity, incident flag and incident description.

### Weather Data
Weather ID, road ID, weather condition, temperature, rainfall, visibility and wind speed.

### Road Data
Road ID, road name, road type, zone, road length, lane count and junction count.

### Signal Data
Signal ID, junction ID, road ID, signal cycle, green time, red time and amber time.

## 🗄️ MySQL Database

Database:

```sql
CREATE DATABASE TraffDB;
USE TraffDB;
```

Main relationship:

```text
road_data
    │
    │ road_id
    ↓
traffic_data
   /  |  \
  ↓   ↓   ↓
incident_data
weather_data
signal_data
```

`road_id` is the main linking key across the traffic-related tables.

## 🐍 Python / Jupyter

Python is used for data cleaning, EDA, feature engineering, machine learning, text processing and AI analytics.

Main libraries:

```text
pandas
numpy
matplotlib
scikit-learn
transformers
openpyxl
mysql-connector-python
```

BERT example:

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
```

## 🤖 Machine Learning

Possible prediction targets:

- Congestion level
- Traffic condition
- Risk level
- Incident likelihood

Workflow:

```text
Raw Data → Cleaning → Feature Engineering → Train/Test Split
→ Model Training → Evaluation → Prediction → Recommendation
```

Potential models include Logistic Regression, Decision Tree, Random Forest and Gradient Boosting.

## 🧠 LLM / RAG

The AI layer can convert structured traffic information into understandable traffic insights.

Example:

```text
Road: Main Road
Vehicle Count: High
Average Speed: Low
Congestion: High
Weather: Heavy Rain
Risk Level: Critical
```

Possible AI output:

```text
Critical congestion detected on Main Road.
Heavy rainfall and high traffic volume are contributing
to reduced vehicle speed. Traffic control intervention
and alternate-route recommendations are suggested.
```

The project can be extended with **RAG (Retrieval-Augmented Generation)** so the LLM answers questions using the project's traffic database, reports, rules and historical information.

# 📈 Power BI Dashboard

## Page 1 — Executive Overview

Purpose: understand the overall traffic situation quickly.

### KPI Cards

- Total Vehicles
- Average Speed
- Average Congestion
- Average Occupancy
- High Risk Roads

### Visuals

- Live Traffic Flow Trend
- Traffic Risk Intelligence
- Top 10 Congestion Hotspots
- Speed vs Congestion
- Traffic Condition

### Slicers

- Zone
- Road Name
- Risk Level
- Weather
- Timestamp

## Page 2 — Incident Analysis

Purpose: analyze traffic incidents and severity.

### KPI Cards

- Total Incidents
- Critical Incidents
- High Severity Incidents
- Accident Count
- Incident Roads

### Visuals

- Incident Type × Severity Matrix
- Incident Impact by Severity
- Incident Severity Distribution
- Top Incident-Prone Roads
- Incident Severity Profile

### Slicers

- Incident Type
- Incident Severity
- Road
- Zone

## Page 3 — Road & Risk Deep Dive

- Top Risk Roads
- Congestion by Road
- Average Speed by Road
- Road Occupancy
- Risk Level by Zone
- Road Risk Ranking
- Traffic Risk Map

## Page 4 — Weather Impact

- Average Rainfall
- Average Temperature
- Average Visibility
- Average Wind Speed
- Rainfall vs Congestion
- Weather vs Traffic Condition

Example:

```DAX
Average Rainfall =
AVERAGE('traffdb 03_weather_raw'[rainfall_mm])
```

## Page 5 — Signal & Junction Analysis

- Signal Cycle Time
- Green vs Red Time
- Junction Congestion
- Signal Efficiency
- Signal Details Matrix

## Page 6 — AI Traffic Intelligence

- Traffic Prediction
- Risk Prediction
- AI Traffic Recommendations
- Congestion Alerts
- High-Risk Road Alerts
- AI-generated traffic summaries

# 📌 Key DAX Measures

```DAX
Total Vehicles =
SUM('traffdb 01_traffic_raw'[vehicle_count])
```

```DAX
Average Speed =
AVERAGE('traffdb 01_traffic_raw'[avg_speed_kmph])
```

```DAX
Average Congestion =
AVERAGE('traffdb 01_traffic_raw'[congestion_score])
```

```DAX
Average Occupancy =
AVERAGE('traffdb 01_traffic_raw'[road_occupancy_pct])
```

```DAX
Total Incidents =
COUNTROWS('traffdb 02_incident_raw')
```

```DAX
Incident Roads =
DISTINCTCOUNT('traffdb 02_incident_raw'[road_id])
```

```DAX
Average Rainfall =
AVERAGE('traffdb 03_weather_raw'[rainfall_mm])
```

# 🔬 Project Hypotheses

### H1 — Traffic Volume vs Congestion
Higher vehicle volume is associated with higher congestion.

### H2 — Speed vs Congestion
Average vehicle speed decreases as congestion increases.

### H3 — Weather vs Congestion
Poor weather conditions can increase congestion.

### H4 — Incidents vs Traffic Risk
High-severity incidents are associated with higher traffic risk.

### H5 — Road Characteristics vs Congestion
Road type, lane count and junction density can influence congestion.

### H6 — Signal Timing vs Traffic Flow
Signal timing efficiency can influence traffic flow and congestion at junctions.

# 📁 GitHub Folder Structure

```text
TrafficPulse-AI/
│
├── README.md
├── data/
│   ├── raw/
│   │   ├── 01_Traffic_Raw.xlsx
│   │   ├── 02_Incident_Raw.xlsx
│   │   ├── 03_Weather_Raw.xlsx
│   │   ├── 04_Road_Raw.xlsx
│   │   └── 05_Signal_Raw.xlsx
│   └── processed/
│
├── notebooks/
│   ├── 01_Data_Cleaning.ipynb
│   ├── 02_EDA.ipynb
│   ├── 03_ML_Model.ipynb
│   ├── 04_BERT_Text_Processing.ipynb
│   └── 05_AI_Analytics.ipynb
│
├── sql/
│   ├── 01_Create_Database.sql
│   ├── 02_Create_Tables.sql
│   ├── 03_Insert_Data.sql
│   └── 04_Analytics_Queries.sql
│
├── powerbi/
│   ├── TrafficPulse_AI.pbix
│   └── dashboard_screenshots/
│
├── models/
├── src/
├── docs/
├── requirements.txt
└── .gitignore
```

# 🛠️ Technologies

| Area | Technology |
|---|---|
| Data | Excel |
| Database | MySQL |
| Programming | Python |
| Analysis | Pandas, NumPy |
| Visualization | Matplotlib |
| ML | Scikit-learn |
| NLP | Hugging Face Transformers / BERT |
| BI | Power BI |
| AI | LLM / RAG |
| Development | Jupyter Notebook |
| Version Control | Git & GitHub |

# 🚀 How to Run

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd TrafficPulse-AI
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Prepare MySQL

```sql
CREATE DATABASE TraffDB;
USE TraffDB;
```

Run the SQL scripts in the `sql/` folder.

### 4. Run Jupyter

```bash
jupyter notebook
```

Open the notebooks from the `notebooks/` folder.

### 5. Open Power BI

Open:

```text
powerbi/TrafficPulse_AI.pbix
```

Refresh the database connection and explore the dashboard.

# 📦 requirements.txt

```text
pandas
numpy
matplotlib
scikit-learn
openpyxl
transformers
torch
jupyter
mysql-connector-python
```

# 🔮 Future Enhancements

- Real-time IoT traffic sensor integration
- Live GPS data
- Streaming data pipeline
- Real-time Power BI dashboard
- Automated traffic alerts
- LLM-powered traffic assistant
- RAG-based traffic question answering
- Route optimization
- Accident risk prediction
- Smart signal timing optimization

# 🌟 Project Highlights

- End-to-end traffic intelligence pipeline
- Multi-domain traffic dataset
- Relational MySQL architecture
- Statistical traffic analysis
- Machine learning prediction
- BERT-based traffic text processing
- Interactive Power BI dashboard
- Road risk intelligence
- Incident severity analysis
- Weather impact analysis
- Signal and junction analysis
- AI-generated traffic recommendations
- RAG-ready architecture

# 👨‍💻 Author

**Gowtham Kumarakannan**

### TrafficPulse AI

**Real-Time Traffic Monitoring, Congestion Prediction & Smart Decision Intelligence**

> **From Traffic Data to Intelligent Decisions.**
