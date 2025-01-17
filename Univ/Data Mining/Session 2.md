#datamining 
# Data Warehousing & Online Analytical Processing

## Data Warehouse Concepts

Data warehouse is similar to database, but it's different in that it's maintained separately from the organitation's operational database, and it acts as a decision support database.
It supports information processing by supporting a solid platform.

> Data warehouse is essentially a <u>structured</u> database.

**Key features of Data warehouse**:
- Historical data
- Data integration
- Optimized for queries
- Read-optimized
- OLAP (Online Analytical Processing)


### Subject Oriented

- Organized around major subjects, such as customer, product, sales
- Provide a simple and concise view around a particular subject, by excluding data that are not useful in the decision making process


### Time variant

- The lifespan of a data warehouse is significantly longer than that of operational systems, because it needs to store data from a historical perspective


### Non-volatile

- Physically separate store data that are transformed from the operational systems
- Operational data does not occur in the data warehouse
	- Requires only two operations in data accessing:
		- Initial loading of data
		- Access of data
	- Does not require transaction processing, recovery, and concurrency control mechanisms




## Data warehouse VS Heterogeneous DBMS

- Traditional Heterogeneous DB integration -> A query driven approach
- A Database usually takes more time to query when we want to analyze data
- A data warehouse is faster in querying but longer in loading the data


## Data warehouse vs Operational DBMS

- OLTP (On line transaction processing)
	- Major task of traditional DBMS
	- Day to day operations: Purchasing, inventory managing, banking, etc
- OLAP (On line analytical processing)
	- Major task of data warehouse system
	- Data analyst and decision making
- Distinct features:
	- Data contents for DBMS is very current, and recent, while DWH has historical data, ranging from 5-10 years old data


==Throughput -> Data/second==


# Data warehouse modelling

- A data warehouse is based on an multidimensional data model, which views data in the form of a data cube
- A data cube, such as sales, allows data to be modelled in multiple dimensions
- Dimension tables such as item (item_name, brand, type) or time (day, week, month, quarter, year)


**Modelling data warehouses**
- Star schema
- Snowflake schema
- Fact constellations

