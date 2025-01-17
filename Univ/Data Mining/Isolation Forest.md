
> State of the art anomaly detection algorithm, famous for it's efficiency and simplicity. It identifies outliers with minimal computational overhead by removing anomalies from a dataset using binary partitioning.


Key concept:
Anomalies are easier to "isolate" compared to normal points in a dataset, because they are rare, and have attributes that deviate from the majority of the data
Isolation forest tries to isolate each data points, and a point that is far from others (Anomalies) will require fewer splits to isolate it, while a point that is closer to many others will require more amounts of splits to isolate.


==Anomaly detection is the backbone of data analysis to identify patterns or events that deviate significantly from the norm in a dataset==

- Isolation forests are unique in that they randomly select features and split them among random values until individual points are isolated
- This "Isolating" process will create partitions shaped like trees that aim to separate anomalies from normal observations
- Anomalies typically require fewer splits to isolate, making them easier to detect.

![[Pasted image 20241127193909.png]]


https://youtu.be/Y1x51i1936M?si=jPDOPzvWabi9Ugcy

How it works:

1. Random partitioning:
	1. The algorithm starts by randomly selecting a feature
	2. Once a feature is selected, a random value within the range of that feature's value is selected as the splitting threshold. 
	3. This process of random feature selection and splitting is repeated recursively until all the data points are isolated into individual partitions or until a maximum depth is reached
2. Isolation path
	Measures how isolated or anomalous a data point is within a tree
	- The isolation path determined by the number of splits it takes to isolate that point within a tree. Anomalies generally require fewer splits to be isolated compared to normal data points.
3. Ensemble of Trees
	Isolation Forest builds an ensemble of isolation trees. Each tree separate data independently, resulting in different isolation paths for each data point across the ensemble of trees
	The anomalies are then identified by evaluating the isolation paths across all trees in the ensemble
4. Anomaly score calculation
	The algorithm computes an anomaly score based on the average path length across all trees in the ensemble. The lower the path length, the higher the anomaly score. And the higher the anomaly score, the more likely that data point is to be an anomaly
5. Thresholding
	We then define a threshold to determine the minimal value of the anomaly score for it to be deemed an anomaly


## Comparison with other algorithms:

1. Distance based methods:
	- Concept: Anomalies are detected based on their distance
	- Comparison:
		- Computational complexity: Distance based can be computationally expensive, especially with larger datasets
		- Advantages: Iforest is more efficient as it doesn't compute pairwise distances
2. Density based methods
	- Concept: Anomalies are detected in low density regions
	- Comparison:
		- Assumption of local density: Density based methods assume that normal data points are in dense areas
		- Advantages: Isolation forest does not rely on density estimations
3. 