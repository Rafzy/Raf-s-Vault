#computervision 
# Edge Detection

Part of convolution btw

## Image gradient

- Gradient equation: $\Delta f =  [\frac{\alpha f}{\alpha x}, \frac{\alpha f}{\alpha y} ]$


## Edge detection

- Roberts operator
- Sobel operators
- Canny edge detections

1. Roberts operator
	Uses 2x2 matrix as the mask
$$
Gy = \begin{bmatrix}
1 & 0 \\
0  & -1
\end{bmatrix}
$$
$$
Gx = \begin{bmatrix}
0 & 1 \\
-1 & 0
\end{bmatrix}
$$

**Gradient magnitude**
$$
\sqrt{ Gx^{2} + Gy^2 }
$$
$$
\theta = \tan^{-(Gy/Gx)}
$$


2. Sobel operator
	uses 3x3 mask

$$
Gx = \begin{bmatrix}
-1 & 0 & 1 \\
-2 & 0 & 2 \\
-1 & 0 & 1 \\
\end{bmatrix}

$$
$$
Gy = \begin{bmatrix}
-2 & -1 & -1 \\
0 & 0 & 0 \\
1 & 2 & 1
\end{bmatrix}
$$


3. Canny edge detector
	- Uses gaussian blur
		5x5 matrix (Can be different doesn't have to be the same like the previous two)
	- Gradient magnitude and direction
		Uses sobel operator
	- non-maximus supression (smoothes the edges)
		take the maximum value
	- Double thresholding
		low threshold
		high threshold
	- edge tracking by hysteresis
		connect the weak edge to strong edge
		remove the weak edge



# GSLC

1. Robert & Sobel (Direction)
$$
\begin{bmatrix}
0 & 100 & 200 \\
100 & 150 & 100 \\
220 & 100 & 0
\end{bmatrix}
$$

2. Robert & Sobel (Direction)
$$
\begin{bmatrix}
120 & 150 & 180 \\
200 & 100 & 240  \\
100 & 200 & 130 
\end{bmatrix}
$$
