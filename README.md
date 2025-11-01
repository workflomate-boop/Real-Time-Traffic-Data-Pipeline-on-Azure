# Real-Time Traffic Data Pipeline on Azure

## Architecture Overview

```
Azure Maps → Function App → Event Hubs → Stream Analytics → Power BI
                              ↓
                         SQL Database → We will use historical data to predict future traffic
```

## 1. Project Planning

### Project Description

This project develops a real-time data engineering pipeline for processing and visualizing live traffic data using Microsoft Azure services. Traffic information from Azure Maps is streamed through Azure Event Hubs, processed with Azure Stream Analytics, stored in Azure SQL Database, and visualized in Power BI dashboards. The system provides complete automation for live traffic insights, congestion trend analysis, and road-performance monitoring.

### Future-Ready Architecture

The Azure SQL Database is designed with a structured schema to support future machine-learning initiatives. The collected historical traffic data will serve as training data for predictive models aimed at forecasting traffic incidents and congestion patterns, enabling proactive traffic management and early-warning systems.

### Objectives

* Stream and process live traffic data in real time.
* Store structured datasets in Azure SQL Database.
* Visualize live KPIs in Power BI dashboards.
* Maintain reliability, scalability, and low latency.
* Prepare data for future predictive analytics and AI integration.

### Tools & Technologies

Azure Maps | Azure Event Hubs | Azure Stream Analytics | Azure SQL Database | Power BI | Azure Storage Account | Azure Log Analytics | Python | SQL

---

## 2. Stakeholder Analysis

| Beneficiary | Type | Benefit / Value Gained |
|-------------|------|------------------------|
| Traffic Authorities | Direct | Access real-time dashboards to monitor congestion and incidents, improving decision-making and emergency response time. |
| Drivers & Commuters | Indirect | Experience smoother travel and fewer delays through optimized traffic flow and incident alerts. |
| Ministry of Transport | Strategic | Use traffic analytics for infrastructure planning, smart-city initiatives, and policy development. |
| Universities & Researchers | Academic | Analyze traffic data for AI-based forecasting and data-engineering studies. |
| Government Decision Makers | Administrative | Utilize aggregated analytics for public safety, mobility planning, and sustainable transport strategies. |

---

## 3. Database Design

**Database Name:** `TrafficSQL`  
**Table Name:** `TrafficData`

### Table Schema Overview

| Field Name | Data Type | Description |
|------------|-----------|-------------|
| `city` | VARCHAR | Name of the city where the traffic event occurred. |
| `latitude` | FLOAT | Latitude coordinate of the traffic event. |
| `longitude` | FLOAT | Longitude coordinate of the traffic event. |
| `description` | NVARCHAR | Text description of the traffic incident. |
| `incident_count` | INT | Number of incidents recorded per time window. |
| `timestamp` | DATETIME | Original timestamp of the event. |
| `window_end` | DATETIME | End time of the one-minute aggregation window. |

### Design Logic

* Real-time traffic data from Azure Maps enters the Stream Analytics job.
* Stream Analytics writes aggregated results into the TrafficSQL database within the TrafficData table.
* Each record represents a processed snapshot of incidents per city and time window.
* This schema supports both real-time visualization in Power BI and historical data analysis for predictive modeling.

---

## 4. UI/UX Design

### Dashboard Features (Power BI)

* **Map Visualization:** Displays live incidents using Azure Maps.
* **KPI Cards:** Show total incidents, number of active cities, and average incidents per city.
* **Line Chart:** Presents incident trends over time.
* **Bar Chart:** Compares incident counts between cities.
* **Table:** Displays recent event data with timestamps and locations.

### User Flow

1. User opens the Power BI dashboard.
2. Selects a city or region of interest.
3. Dashboard automatically updates with live traffic data.
4. User reviews metrics, map visuals, and performance trends.
5. Insights are used for real-time operational decisions.

### Design Principles

* **Clarity:** Clean layout and minimal distractions for faster interpretation.
* **Interactivity:** Real-time refresh and filters by city or time.
* **Consistency:** Unified color palette and structured grid layout.
* **Scalability:** Ready for integration with predictive analytics visuals in the future.

