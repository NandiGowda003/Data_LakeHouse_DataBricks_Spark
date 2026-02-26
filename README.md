# Data_LakeHouse_DataBricks_Spark
About End-to-end Data Lakehouse project built on Databricks, following the Medallion Architecture . The workflows using Spark, PySpark, SQL, Delta Lake, and Unity Catalog.



# 🏗 High Level Arhitecture

<img width="691" height="768" alt="Lakehouse_Architecture drawio" src="https://github.com/user-attachments/assets/20d319f7-b0ea-4f10-a9a0-988fdfed2ec6" />

🥉 Bronze Layer
* Raw data ingestion
* Schema inference and storage as Delta tables

🥈 Silver Layer
* Data cleaning and standardization
* Type casting and validation

🥇 Gold Layer
* Dimensional Data Model (Business Transformation)
* Ready for analysis
