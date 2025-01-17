# Data Preparation

Several steps needed to prepare data:
- Data Quality Measure
- Data Cleaning
- Data Integration

## Data Quality Measure

There are several quality measures that we have to ensure as a part of Data preparation, these include:
- Accuracy
	Checking whether the data we have gathered is accurate and is correct or not in regards to facts
- Completeness
	Whether the data is complete or not, or whether there are some unavailable data or incomplete values within the data
- Consistency
	We must check the consistency in the data, for example, does the timeline in the data keep a consistent pace, or whether some of the data have been modified or not
- Believability
	The measure of how believable the data that we have is correct or not, and how trustable is it that we can use this data for further processes
- Interpretability
	How interpretable the data is, both for humans and for machine, typically the data needs to follow a certain baseline format for it to be interpretable


## Major tasks in Data Preprocessing

- **Data Cleaning**
	Data cleaning involves taking the data that we have, and rid of any inconsistencies within the data, like any null or missing values, remove outliers, etc. This step is important because it factors in the Consistency of the data we want to work with. And it's especially important if we want to integrate the data to any machine learning tasks.
- **Data Integration**
	This task involves integrating several data sources like databases, data cubes, or directly from files to our implementation
- **Data Reduction**
	Data reduction involves reducing the "complexity" of the data, like reducing dimensionality, or compressing the data. This factors in the Interpretability of Data Quality measure, because data with high dimensionality or high complexity makes it very hard to work with.
- **Data transformation**
	This task involves transforming the data we have to improve the interpretability of the data that we have, for example like normalizing the data, and concept hierarchy generation.



# Data Cleaning

> Typically, the data we get from the real world is full of inconsistencies, like potentially incorrect data, missing values, error from human or computer while gathering the data, or instrument faultiness.

Several "incorrectness" that real world data may contain:
- Incomplete
- Noisy
- Inconsistent
- Intentional

Due to this, we must take further steps in data cleaning to address these incorrectness from real world data.

## Missing values

There are several reasons to why data may be incomplete while gathering data, these include:
- Faulty equipment
- Deleted due to the data being inconsistent with other recorded data
- Data not being entered due to misunderstandings
- Certain data not being considered important
- Changes in the data not being registered

**Handling missing values**
there are several ways we can address the missing values:

- Ignore the tuple/row completely
	We can ignore the whole tuple with the missing value completely, this is usually done when the class label is missing. However, this is not effective when the missing values per attribute varies, or when the number missing value is too large that it considerably impacts the size of the data
- Fill the missing value
	We can fill in those missing values either manually or automatically with several techniques:
	- Global constant
	- Measure of central tendency (Like mean or median, this is only possible for numerical value attributes)
	- Attribute mean or median for all samples belonging to the same class as the given tuple
	-  Use the most probable value (Inference based like bayesian formula or decision tree, this technique usually is more computationally heavy.)


## Noisy Data

Noisy data means data that contains random errors or unfit variance in a measured variable. There are several causes to this, such as:
- Faulty data collection instruments
- Data entry problems
- Data transmission problems
- Limitations in technology
- Inconsistency in naming conventions

**Handling noisy data**
- Binning (Discretization)
	Binning is a technique used to transform continuous data into discrete bins or intervals. Usually done with numerical data. This is useful to reduce noise in data. There are three methods in binning:
	- Equal-width binning
	- Equal-depth/frequency binning
	- Custom binning
- Regression
	Regression is a technique used to smoothen out the data by fitting it into regression functions. This regression functions can vary depending on the shape of the data and how we want to fit it.
	- Linear-regression
	- Non-linear regression
- Clustering
	Involves clustering the data, can be done manually or usually done with machine learning models, to detect and remove outliers in the data
- Combined computer and human inspection
	Manually detecting outliers and suspicious values to remove them from the data.

### More on binning

- Equal-width partitioning
	Binning that divides range into N intervals of the same size
	Calculate the width of intervals:
	$W = \frac{B-A}{N}$
	where:
	$B$ = highest attribute
	$A$ = Lowest attribute
	Pros:
	- The most straightforward method
	- easy to execute
	Cons:
	- Outlier may dominate presentation
	- Doesn't handle skewed data

- Equal depth (frequency)
	Binning that divides the data into N intervals, with each interval containing the same number of samples
	Pros:
	- Good data scaling
	Cons:
	- Tricky for categorical attributes

Example of binning:

![[Pasted image 20241007134758.png]]


## Data cleaning as a process

**Data discrepancy Detection**
How we can detect any discrepancy or mistakes within the data we want to work with
- Use metadata
- Check field overloading
- Check uniqueness, consecutive, and null rule
- Use commercial tools

**Data migration and integration**
- Use data migration tools
- ETL Tools to specify transformations through a GUI

# Data Integration

> How we integrate Multiple sources of data for our purpose

**Data Integration**
	Involves combining data from multiple sources into one coherent store of data. Usually data that correlates with one another or of the same topic. 
**Schema integration**
	Involves integrating metadata from different sources. (Metadata are data that explains the main data we work with)

Several problems with data integration:
- Entity identification problem
	Problem with identifying real world entities from multiple data sources. For example bill clinton might be assumed to be related with william clinton
- Detecting and resolving data value conflicts
	Attribute values from different sources may be different even for the same real world entities. This may be because different representations, different scales, like one using the metric system and one using the american system.
- Data redundancy
	Data redundancy may occur when we integrate multiple databases that contains a large amount of the same or similardata.
	- Object identification (The same attribute may have different names in different databases, or the way they're interpreted)
	- Derivable data (One attribute may be a "derived" attribute of another data)
	These data redundancy may be detected using correlation analysis and covariance analysis.
	Being careful when integrating data from multiple sources may also reduce the redundancies and inconsistencies after being integrated


