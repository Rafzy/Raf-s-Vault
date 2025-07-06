
# Analyzing Feature value and feature space

![[image-74.png|502x361]]

We can imagine an image with green and red apple with a dark background. 
We can plot the pixels of this image on the graph
By doing so, we can classify the objects in the image.

The red and greed is called a feature space.
Feature value -> Amount that can classify the category

![[image-75.png|504x332]]


**Classification methods**

There are several methods for classification

"Maximum distance classifier"
We take point $x_{0}$, and we think about which category to assign that $x_{0}$ point to. Minimum distance classifier decides which group to assign $x_{0}$ to based off of the closest distance. 

![[image-81.png|483x334]]

We can consider the probability density in this situation, for point $x_{0}$, there are two categories, the point may belong to, so we get a probability density for two clusters. The probability density will increase, the shorter distance is from the point to a certain cluster, so for this case, the probability density may look like this:

![[image-82.png|492x310]]

So, for this case, because point $x_{0}$ is closer to cluster 1, point $x_{0}$ is more likely to be categorized to cluster 1 compared to cluster 2