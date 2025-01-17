# Handling missing Data (Review)

**Numerical/Categorical**
if percentage of missing data > 10%, we delete the column
if <= 10%, we check the data distribution
if the distribution is normal, we use mean (numerical)
if skewed, we use median (numerical)
we use mode for categorical data


# Data Transformation

- We use functions to transform our data
- Methods:
	- Smoothing
	- Aggregating
	- Etc


## Normalization

>"Normalizing" The data with functions

- Min Max Normalization
	Bad with outliers
$$
v' = \frac{v-min_{a}}{max_{a}-min_{a}}(newmax_{A} - newmin_{b})+newmin_{A}
$$

- Z-score normalization
	Use mean, and standard deviation
$$
v'=\frac{v-\mu_{a}}{\sigma_{a}}
$$

- Normalization by decimal scaling
$$
v' = \frac{v}{10^j}
$$


## Discretization

>Divide the range of a continuous attribute into intervals

These labels can then be used to replace the actual data values

- Binning
- Histogram
- Clustering
- Etc


# Data Reduction (Data Compression)

- Data Compression: String Compression or audio/video compression
- Type of compression



# Type of Sampling

- Simple random sampling
- Sample withour replacement
- Sampling with replacement
- Stratified sampling


# Data Reduction

- Obtain a reduced representation of the dataset that is much smaller in volume but yet produces the same analytical result



# Exercise

