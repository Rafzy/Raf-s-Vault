
1. Find OLTP and OLAP use cases in real world, each 3
	- **OLTP** (DBMS)
		Used for real time, large volumes of database transactions daily, Usually use a relational database or general DBMS.
		Use cases:
		- Banking system
		  Banking systems require handling large amounts of transactional data every day, like millions of users doing withdrawals, transfers, etc. Thus banking system requires a DBMS for it's OLTP to handle those transactions
		- E-commerce platforms
		  Similar to the banking system, e-commerce requires OLTP to handle large amounts of data transactions every day, it differs in that e-commerce usually needs to track product inventories, transactions made by users to different vendors, and keeping track the amount of money that the buyer needs to pay to the vendors daily.
		- Healthcare management systems
		  Healthcare systems require real time patient records, appointments, billings, or clinical data to be tracked and managed, requiring an OLTP to track those transactions
	- **OLAP**
		Typically used by data analysts to report, analyze, and predict data. Example like data warehouse.
		Use cases:
		- Financial analysis and predictions
			OLAP helps finance departments in analyzing historical financial data to predict forecasts for future trends and potentially help in budgeting
		- Customer behavior analysis
			OLAP helps in marketing departments in predicting customer behaviors in shopping habits by analyzing data from customer historical purchases, or vendor sales.
		- Business reports
			OLAP systems are usually used in businesses to analyze historical business data, like the increase or decrease in company's net worth or stock prices, to massively help in decision making within the company

2. Find the differences between Data Warehouse vs Data Mart vs Data Lake + when to use them.
	- **Data warehouse**
		a structured form of database or repository, usually stores larger volumes of data compared to regular DBMS from multiple sources, it's designed for analyzing data, reporting, and Business Intelligence
		When to use:
		- When we want to do analysis on a centralized, structured repository on several fact tables on different subjects, to help in overall decision making or predictions
	- **Data Mart**
		A subset of data warehouse, where it is more specialized on a single line of subject, or business unit. It's usually tailored to meet the needs of specific users or teams
		When to use:
		- We use data mart when we need data analysis for a specific subject, or department for very focused analysis for that department only.
	- **Data Lake**
		Data lake is a more "unstructured" version of data warehouse, it can store large amounts of raw, unstructured, semi-structured, or structured data, all of them in their native formats. It's designed to store different kinds of data, from relational data, to documents, and even images. It becomes a sort of amalgamation of raw un-processed data.
		When to use:
		- We use data Lake when we need a scalable and flexible repository that can store large amounts of raw and diverse data, that will be used for complex and advanced analysis, or big data processing and machine learning.


	a. Find the technology stack needed to implement each of them (specific products in cloud/other)
	- **Data warehouse**
		- Relational Databases
		  Microsoft SQL Server
		- ETL tools
		  AWS Glue, Microsoft SSIS
		- Data integration
		  Apache Airflow, Azure Data Factory
		- Data modeling
		  Erwin Data Modeler, Oracle SQL Developer Data Modeler
		- Analytics
		  Tableau, Qlik Sense
	- **Data mart**
		- Relational Database
		  SQL Server, MySQL, Microsoft SQL Server
		- Analytics
		  Tableau, Qlik Sense
	- **Data Lake**
		- Distributed Storage System
		  Google cloud storage, Amazon S3, Azure Data Lake Storage
		- Bid Data Processing Framework
		  Apache Spark, AWS EMR
		- Stream Processing
		  Apache Kafka, Apache Flink, AWS Kinesis
		- Data Catalog
		  Apache Atlas, AWS Glue Data Catalog
		- ETL Tools
		  Apache Nifi, AWS Glue
		- Query Engines
		  Presto, Apache Hive, Amazon Athena