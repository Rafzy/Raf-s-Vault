
# Data Mining

**Definition:**
> The process of discovering patterns, models, and other kinds of knowledge in large datasets

Other terms:
- Knowledge mining from data
- Knowledge discovery from data
- Pattern discovery

Data mining hierarchy in business intelligence
![[Pasted image 20241022145141.png]]


## KDD (Knowledge Discovery)

> The comprehensive process of extracting meaningful information and pattern from large volumes of data. KDD consists of steps to transform raw data into valuable insight, which can inform decision making accross various domains

**Steps:**
- Data preparation
	- Data cleaning
	- Data integration
	- Data transformation
	- Data selection
- Data mining
- Pattern/model evaluation
- Knowledge presentation

![[Pasted image 20241022145745.png]]

In general, data mining tasks can be divided into two categories:
- **Descriptive data mining:**
	Focuses on summarizing and understanding data, the goal is to find patterns, correlations, or trends within existing data
- **Predictive data mining:**
	Aims to make predictions about future outcomes based on historical data. typically includes training models that can forecast or make predictions of future data points

Specific tasks in data mining:
- Multidimensional data summarization
	Condense large datasets with multiple dimensions into a summary form, making it easier to understand
- Mining frequent patterns, associations, and correlations
	Discovering relationships and patterns within a dataset (i.e. what are the frequently bought items along with water in walmart)
- Classification and regression for predictive analysis
	Techniques in predictive analysis, to predict category, or continuous numerical values.
- Clustering analysis
	Group unlabeled data to form new vategories
- Deep learning
	Broad applications in Computer Vision, NLP, etc
- Outlier analysis
	Identify data points that significantly differ from the rest of the dataset.


## Confluence of multiple disciplines

Integration of knowledge, methods, and tools to effectively analyze and extract insights from large data sets:

- Machine Learning
- Pattern recognition
- Visualization
- ALgorithm
- High-performance computing
- Applications
- Information retrieval
- Data warehouse
- Database systems
- Statistics

## Data Mining Application

- Business Intelligence
- Web search engine
- Biological & Medical data analysis
- Collaborative analysis
- Recommender system


# Data warehousing

Definition:
> A **separate** database from an organization's operational database whose purpose is to support decision making. It supports **information processing** by providing a solid platform of consolidated, historical data for analysis

Data warehouse characteristics:
- Subject oriented 
	each data warehouse is designed for a specific subject or area of interest within an organization
- Integrated 
	The sources from the data collected are integrated from various heterogeneous sources and then standardized, and data cleaning and data integration techniques are applied
- Time variant 
	A data warehouse is designed and structured to capture changes over time throughout the history, and the time horizon of a data warehouse is significantly longer than operational database/systems
- Nonvolatile 
	Data inside of the data warehouse is not easily altered or deleted. The data remains stable over time

**Multi tiered architecture**
- Top tier: Front end tools
- Middle tier: OLAP Server
- Bottom tier: Data warehouse server
- Data


**Data warehouse vs Heterogeneous database**
Heterogeneous database:
- Query driven
- wrappers/mediators
- client side

Data warehouse:
- Update driven
- High performance
- Information from heterogeneous sources is integrated in advance and stored in warehouses for direct query and analysis


## OLAP vs OLTP

> OLAP and OLTP are both fundamental systems used in database management, both serve different purposes

**OLTP (On-line transaction processing)**
Major tasks for relational DBMS 
- Purpose:
	Designed for day-to-day transactional operations such as inserting, updating, deleting, and retrieving small amounts of data. Example: Bank transactions, Inventory management, etc

- Characteristics:
	- Volume: Deals with small frequent transactions
	- Type: Current (Very up to date), Highly detailed and operational data
	- Example: Customers orders, ATM Withdrawals
	- Suitable for DBMS

**OLAP (On-line analytical processing)**
Major tasks for data warehouse system
- Purpose:
	Designed for complex analysis, large data queries, and report to support decision-making. OLAP systems are focused on aggregating and analyzing large volumes of data from multiple sources to provide insight

- Characteristics::
	- Volume: Large, historical data
	- Type: Multidimensional, aggregated data, usually stored in data warehouses
	- Example: Sales data over the years, Customer segmentation, financial summaries
	- Suitable for data warehouse

## Data warehouse modelling

> Data warehouse is based on a multidimensional data model which views the form of a data cube


- Data cube (Ex: Sales) 
	Multidimensional array that organizes data in multiple dimensions, allowing users to analyze data from different perspectives

- Dimension tables (Ex: item(item_name, brand_type) or time(day, week, month, quarter, year))
	A "slice of the data cube", it stores descriptive information about the dimensions in a data warehouse, it provides context or "labels" for the data in fact table.
- Fact tables (Ex: dollars_sold) -> contains measures and keys to each of the related dimension tables
	Core table in data warehouse, it contains the **measurable** and **quantitative data** of interests like sales, revenues, or units sold. Fact tables contain facts and foreign keys that link to the dimension tables

**Data warehouse modelling**
- Star schema
	Fact table in the middle connected to a set of dimension tables, the simplest form of data warehouse modelling, however this model can lead to dimension tables not being normalized and which leads to redundancy
	![[Pasted image 20241022154226.png]]

- Snowflake schema
	refinement of star schema where some dimension tables is normalized to a set of smaller dimensional tables. This approach reduces redundancy by storing dimension data in smaller, more granular tables. This approach is better in reducing redundancy, but can lead to slower query performances due to more joins
	![[Pasted image 20241022154332.png]]

- Constellation fact table
	Multiple fact table shares dimension tables, viewed as constellation of stars. It's a combination of multiple star schemas. it allow analysis of multiple, interrelated business processes, but it's complex schema design can make it harder to maintain and understand
	![[Pasted image 20241022154414.png]]


# Data and Measurements

## Data

> Collection of objects and their attributes

Attribute -> Characteristics of an object
Collection of attributes describe an object

![[Pasted image 20241022160146.png]]



**Types of attributes:**

- Categorical:
	- Nominal 
	- Ordinal
- Numeric:
	- Interval-scaled -> Range between values is meaningful, but 0 point is arbritrary
	- Ratio-scaled -> The difference and ratios between values are meaningful, and a true zero point indicates the complete absence of something being measured


Nominal -> Distictness
Ordinal -> Distinctness & Order
Interval -> Distinctness, Order, & Addition
Ratio -> Distinctness, Order, Addition, & Multiplication


## Statistics of Data

> We do this to understand the data: central tendency, variation, and spread

- **Central tendency characteristics**
	Refers to the "central" or "typical" value in a dataset. It gives an idea of where most data points are located or the general trend of the data
	Ex: Mean, median, and mode
- **Data dispersion characteristics**
	Refers to how spread out the values in a dataset are, it indicates the extent to which data points differ from each other and from the central values
	Ex: Quantiles, interquartile range, variance, standard deviation

## Central Tendency

**Mean**
![[Pasted image 20241022161130.png]]

**Median**
![[Pasted image 20241022161204.png]]

**Mode**
![[Pasted image 20241108083834.png]]

**Midrange**
![[Pasted image 20241108083847.png]]

## Symmetric vs Skewed Data
![[Pasted image 20241108083930.png]]


## Dispersion of Data

- **Range**
	The difference between the largest and smallest values
- **Quartiles**
	Q1 (25th percentile), Q3 (75th percentile)
- **Inter quartile range**
	IQR = Q3 - Q1
- **Five number summary**
	Contains: min, Q1, median, Q3, max
- **Boxplot**
	End of the box are the quartiles, median is marked, add whiskers and plot outliers individually
- **Outlier**
	Value higher/lower than 1.5 x IQR


**Variance**

![[Pasted image 20241022161326.png]]


# Data Preparation

![[Univ/Data Mining/Session 4|Session 4]]


## Data Transformation

- Smoothing: Remove noise
- Attribute/feature construction: New attributes constructed from the given ones
- Aggregation: Summarization, data cube construction
- Normalization: Scaled to fall within a smaller, specified range
- Discretization: concept hierarchy climbing


### Normalization

![[Pasted image 20241108090722.png]]


### Discretization

>Divides the range of continuous attribute into intervals

- Reduce data by discretization
- Supervised vs unsupervised
- Split vs merge
- Discretization

Methods:
- Binning
- Histogram analysis
- Clustering analysis
- Decision tree analysis
- Correlation analysis


## Data Reduction

> Reduced representation of the dataset that is much smaller in volume, but reduces the same analytical result

Methods for data reduction:
- Parametrics
	Summarizing data by assuming that it follows a specific distribution or model. Relies on estimating a set of **parameters**
	Ex:
	- Mean and variance for Normally distributed data
	- Linear regression models
	- PCA

- Non-parametric data reduction
	Does not assume any specific distribution for the data, it focuses on reducing data size or complexity without imposing a strict model.
	Ex:
	- Histograms
	- Clustering
	- Sampling



### Dimensionality

Curse of dimensionality:
- When dimensionality increases, data becomes sparse
- Density and distance between points, becomes less meaningful
- The possible combinations of subspaces will grow exponentially


We reduce dimensionality to avoid the curse of dimensionality

**Methodologies**
- Feature selection
- Feature extraction
