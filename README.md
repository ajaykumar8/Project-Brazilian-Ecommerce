# **Project: Brazilian E-commerce Data Engineering Pipeline**

This project implements an end-to-end data engineering pipeline to process the [Olist Brazilian E-commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

The primary goal is to ingest raw data from multiple CSV files, orchestrate the data flow, transform and clean the data using a modern data stack, and load it into a structured database ready for analytics and business intelligence.

## **Architecture**

The data pipeline is visualized in the Architecture Diagram.png file included in this repository. The general flow is as follows:

1. **Ingestion:** Raw e-commerce data (customers, orders, payments, etc.) is ingested.  
2. **Orchestration:** An orchestrator, such as Azure Data Factory, manages the pipeline's execution, handling dependencies and scheduling. The ForEachInput.json file is likely a configuration for such a pipeline.  
3. **Transformation:** The core data transformation logic is executed in **Azure Databricks**. The Databricks Awesome Code for Tranformation.html file (an exported Databricks notebook) contains the PySpark or Spark SQL code used to clean, join, and aggregate the data.  
4. **Loading:** The transformed, high-quality data is loaded into a final destination, such as an Azure SQL Database or Synapse Analytics warehouse.  
5. **Analysis:** The final structured data is now ready to be queried using SQL (as seen in sql code.txt) for reporting and dashboarding.

## **Technologies Used**

This project utilizes a modern, cloud-based data stack, primarily centered on Microsoft Azure:

* **Azure Data Factory:** For pipeline orchestration and data movement.  
* **Azure Databricks:** For large-scale data transformation using Spark (PySpark and Spark SQL).  
* **Azure SQL Database / Azure Synapse Analytics:** As the final data warehouse/database for serving analytical queries.  
* **Python:** Used in the Jupyter and Databricks notebooks (Pandas, PySpark).  
* **SQL:** For data querying, transformation, and analysis.

## **Repository Structure**

├── Data/                     \# (Assumed) Directory for raw .csv data files  
├── Architecture Diagram.png  \# Visual diagram of the data pipeline  
├── DataIngestionToDB.ipynb   \# Jupyter Notebook for initial data ingestion into a DB  
├── Databricks Awesome Code for Tranformation.html \# Exported Databricks notebook with core ETL logic  
├── ForEachInput.json         \# Configuration file for pipeline (e.g., Azure Data Factory)  
└── sql code.txt              \# Sample SQL queries for analysis

## **How to Use**

To set up and run this pipeline, you would typically follow these steps:

1. **Clone the Repository:**  
   git clone \[https://github.com/ajaykumar8/Project-Brazilian-Ecommerce.git\](https://github.com/ajaykumar8/Project-Brazilian-Ecommerce.git)

2. **Deploy Azure Resources:**  
   * Set up an Azure Data Factory instance.  
   * Set up an Azure Databricks workspace.  
   * Set up an Azure SQL Database or Synapse Analytics instance to serve as the data sink.  
3. **Configure Pipeline:**  
   * Upload the raw data to a storage account (e.g., Azure Blob Storage) accessible by your services.  
   * Import the Databricks...html notebook into your Databricks workspace.  
   * Configure your Azure Data Factory pipeline to connect to your resources, using the logic from DataIngestionToDB.ipynb and the Databricks notebook as steps.  
4. **Run Pipeline:**  
   * Trigger the Azure Data Factory pipeline to execute the full end-to-end data ingestion and transformation.  
5. **Analyze Data:**  
   * Connect a BI tool (like Power BI) or run queries from sql code.txt against your final database to analyze the processed data.