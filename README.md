# Data_LakeHouse_DataBricks_Spark
A production-style Data Lakehouse built on Databricks, designed and implemented independently using the Medallion Architecture (Bronze → Silver → Gold). The workflows using Spark, PySpark, SQL, Delta Lake, and Unity Catalog.


# Tools Used
# Component                    Technology
* DataProcessing       -    Apache Spark / PySpark
* Compute & Notebooks  -    Databricks
* Storage Format       -    Delta Lake
* Orchestration        -    Databricks Workflows
* Governance           -    Unity Catalog
* Language             -    Python / SQL

# 🏗 High Level Architecture

<img width="691" height="768" alt="Lakehouse_Architecture drawio" src="https://github.com/user-attachments/assets/20d319f7-b0ea-4f10-a9a0-988fdfed2ec6" />

# 🔑 Key Design Decisions 
1. Medallion Layer Design
Chose a strict 3-layer separation rather than a 2-layer approach because business oriented data has high variability in quality — separating raw from cleaned ensures no data loss while maintaining a reliable analytics layer.
2. Unity Catalog Schema Strategy
Designed the catalog to mirror the medallion layers (bronze/silver/gold as schemas within one catalog). This makes access control simpler — different teams can be granted access at the schema level without exposing raw data to analysts.
3. Delta Lake Schema Design
Used schema enforcement on Silver and Gold layers with schema evolution allowed only on Bronze. This prevents accidental schema drift breaking downstream dashboards while still handling upstream source changes gracefully.
4. Orchestration with Databricks Workflows
Designed a dependency-based DAG using Databricks Workflows where Gold jobs only trigger after Silver jobs complete successfully — ensuring data quality gates between layers.

# 📳 Data Modeling diagram
<img width="1500" height="558" alt="data_Model_StarSchema" src="https://github.com/user-attachments/assets/2a22409d-d5f7-47ed-a27f-afbc6f59b6e2" />

# ➕ Data integration
<img width="861" height="571" alt="Data_integration drawio" src="https://github.com/user-attachments/assets/784c138e-f062-405f-86f1-7c3b58077956" />




# 🚀 How to Run

* Set up Databricks workspace with Unity Catalog enabled
* Clone this repo into your Databricks workspace
* Run notebooks in order: Bronze → Silver → Gold
* Configure Databricks Workflow using the provided DAG setup
* Connect Power BI to Gold layer tables via Databricks SQL connector

# data pipeline & Orchestration timeline

<img width="1532" height="617" alt="pipeline_timeline" src="https://github.com/user-attachments/assets/fd549ab8-d804-4965-9e10-838a3f2e7700" />




# 💡 What I Learned & Applied

* Designing a production-grade lakehouse from scratch, not just following steps
* Making real architectural trade-offs (e.g., schema enforcement strategy)
* Unity Catalog governance — catalog/schema/table level access design
* Thinking about downstream consumers (Power BI) when designing Gold schemas
  
# Note: 
  While this project was inspired by course learning, 
Still the architecture design, data flow, Unity Catalog structure, and Delta Lake schema were independently designed based on real-world best practices.
