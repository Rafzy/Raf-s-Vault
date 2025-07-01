
Second differential laplacian:
![[image-76.png|603x94]]

We use the absolute value of laplacian, because it's not easy to detect the zero cross point.
The peak value of laplacian is located near the edge, so the edge can be detected by locating the peak value of laplacian.

![[image-77.png|591x329]]

This is an example of applying laplacian operator.
We take the absolute value of laplacian operator, and the edge can be located by found by searching for the pixel where the score is above the threshold

![[image-78.png|600x340]]

"Contour extraction using template matching"
The edge of an image is rotated to create a template image. The score is calculated by using the template images as operators. 

![[image-79.png]]


"Histogram"

The graph of a frequency is called a histogram

"Mode method"
We can assume that the mode is bimodal, then we set the value at the valley of the histogram

The P-tile method is an image segmentation technique that determines an optimal threshold value for separating objects from backgrounds in digital images.
The method assumes that the object to be extracted occupies the lower brightness regions and that its approximate pixel area is known beforehand. It calculates the area ratio p = S₀/S, where S₀ represents the object's pixel count and S represents the total image pixels. Using this ratio with the image's brightness histogram, the method identifies the threshold value T that effectively separates the object area from the background area.

The discriminant analysis method determines an optimal threshold by dividing image pixels into two classes (object and background) and calculating within-class and between-class variances using statistical formulas. The method iteratively adjusts the threshold T to maximize the ratio of between-class variance to within-class variance, ensuring optimal separation between the object and background regions.

![[image-80.png]]

