# End-to-End Data Pipeline using Microsoft Fabric

## 📌 Overview

This project demonstrates the design and implementation of an end-to-end data pipeline using Microsoft Fabric for a retail business scenario.

The pipeline follows the Medallion Architecture (Bronze, Silver, Gold) to transform raw transactional data into meaningful business insights.

---

## 🏗️ Architecture

The pipeline is structured into three layers:

### 🟫 Bronze Layer

* Ingest raw data from external CSV sources
* Store data in Parquet format
* Partition data by ingestion date
* No transformation is applied to preserve raw data

### 🟨 Silver Layer

* Clean and validate data
* Remove invalid records (failed orders, invalid feedback scores)
* Store invalid data in quarantine tables
* Ensure data quality for downstream processing

### 🟥 Gold Layer

* Transform and aggregate data for business analysis
* Calculate key metrics such as:

  * Monthly revenue (VND)
  * Promotion effectiveness
* Implement Star Schema for analytical modeling

---

## 🔄 Pipeline Design

The system uses modular pipelines for orchestration:

* Bronze Pipeline → Data ingestion
* Silver Pipeline → Data cleaning
* Gold Pipeline → Data transformation
* Master Pipeline → Controls the full workflow using invoke pipeline

This design improves maintainability and allows rerunning individual stages independently.

---

## 📊 Data Modeling (Star Schema)

The Gold layer includes a simplified Star Schema:

* **Fact Table**

  * `fact_sales`: stores revenue and transaction metrics

* **Dimension Tables**

  * `dim_product`: product information (items)
  * `dim_location`: geographical data
  * `dim_date`: time-based attributes

This structure enables efficient analytical queries and supports business intelligence use cases.

---

## 🧠 Key Features

* End-to-end pipeline implementation
* Medallion architecture design
* Data cleaning with quarantine handling
* Business KPI calculation
* Star Schema data modeling
* Modular pipeline orchestration

---

## ⚙️ Technologies Used

* Microsoft Fabric (Lakehouse, Pipelines)
* PySpark
* Delta Lake
* Parquet

---

## ⚠️ Notes

This project was developed and tested in a Microsoft Fabric trial environment.
Due to resource limitations, some advanced features such as incremental processing and monitoring are described conceptually.

---

## 📷 Project Assets

* Pipeline screenshots: `/pipelines/`
* ERD diagram: `/erd/star_schema.png`
* Notebooks: `/notebooks/`

---

## 🚀 Conclusion

This project demonstrates how to design a scalable data pipeline and transform raw data into structured insights for business decision-making.

