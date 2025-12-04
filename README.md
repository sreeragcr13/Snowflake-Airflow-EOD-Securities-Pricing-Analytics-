# **🏦EOD Securities Pricing Analytics with Snowflake & Airflow**

## 📖 **Project Overview**

**RBF**, a global investment firm, performs **End-of-Day (EOD)** pricing analysis to evaluate market liquidity, sector rotations, ETF performance, and watchlist stock trends. Previously, analysts manually collected pricing data from multiple sources and prepared reports, leading to delays in daily reporting. This operational gap affects:

- **Daily portfolio review meetings**
- **Overnight risk adjustments**
- **Monitoring sector liquidity shifts**
- **Tracking watchlist stock momentum**

The objective of this project is to **automate** the EOD pricing analysis for U.S. securities and provide **multiple curated analytic views** to support trading, risk management, and research.

---

## 🎯 **Objectives**

- Build a fully automated **data pipeline** for processing **EOD securities pricing** and **liquidity data**.
- Generate insights into:
  - **Equity & ETF liquidity**
  - **Watchlist performance & momentum**
  - **Volume & traded-value intelligence**
  - **Sector-level liquidity contributions**
  - **Daily top market movers**
- Enable **automated daily reporting** for decision support using **Power BI**.
  
---

## 🧰 **Tools & Technologies**

| **Tool / Service**         | **Purpose**                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Apache Airflow**          | Orchestrate the workflow with automated DAGs for data ingestion and processing |
| **Polygon.io**              | Data source for EOD securities pricing data                                  |
| **AWS (S3)**                | Store raw and processed files                                                |
| **Snowflake**               | Data warehouse for standardized and validated pricing data                   |
| **Power BI**                | Visualize analytical insights and trends                                     |
| **Python**                  | Scripting for Airflow tasks and data processing                              |
| **Slack**                   | Notify users about task statuses and pipeline updates                        |

---

## 🧱 **Pipeline Architecture**

![Project Architecture](project_architecture.png)

### **Data Flow:**
1. **Data Ingestion**: Automated **Airflow DAGs** download **EOD data** from **Polygon.io**.
2. **Data Storage**: Raw data is stored in **AWS S3**.
3. **Data Processing**: 
   - **Snowflake** processes the data (cleaning, validation, transformation).
   - Data is loaded into **Snowflake**'s **RAW**, **CORE**, **DIM** and **FACT** schemas for detailed analysis.
4. **Data Reporting**: 
   - **Power BI** connects to **Snowflake** for real-time reporting and decision support.
   - **Slack** notifications for status updates and alerts.

---

## 📝 **Daily Load Process in Snowflake**

### **Data Pipeline Phases:**

1. **RAW**: Land data directly from Polygon.io (CSV format) into **S3**.
2. **CORE**: Clean and validate the data before processing.
3. **DIM**: Build conformed dimensions for analysis (e.g., **DIM_SECURITY**, **DIM_DATE**).
4. **FACT**: Build **fact tables** for reporting on **EOD** pricing and liquidity.

The pipeline includes:

- **Delta checks** to ensure fresh pricing every day.
- **Merge operations** to update the **CORE**, **DIM**, and **FACT** tables in **Snowflake**.

---

## ⚙️ **Airflow DAGs for Automation**

The **Airflow DAG** orchestrates the entire pipeline, including:

1. **Data download** from **Polygon.io**.
2. **Verification of downloaded data**.
3. **Upload to S3**.
4. **Snowflake ETL** tasks to load the data into **RAW**, **CORE**, **DIM**, and **FACT** schemas.
5. **Slack notifications** for updates.


---


## 📊 **Power BI Reporting Layer**

Power BI dashboards offer insights into:

- **Equity & ETF Liquidity**
- **Watchlist Stock Performance**
- **Volume & Traded-Value Trends**
- **Sector-level Liquidity Contribution**
- **Daily Top Market Movers**

![Market Liquidity Report](securities_market_report1.jpg)
![Market Liquidity Report](securities_market_report2.jpg)

---

## ✅ **Outcomes**

- 🚀 Automated daily EOD data ingestion and processing
- 💡 Real-time insights into market liquidity, sector performance, and watchlist stocks
- ⏱️ Faster detection of trading opportunities and risk adjustments
- 🔐 Enhanced decision-making capabilities with actionable insights

---

Copyright©️ Codebasics Inc. All rights reserved.
