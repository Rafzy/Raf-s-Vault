
# Image Processing II

## Matrix Translation

Example of image multiplication
$$
\begin{bmatrix}
2 & 0 \\
0 & -1
\end{bmatrix}
\begin{bmatrix}
1 \\
3
\end{bmatrix}
=
\begin{bmatrix}
2 \\
-3
\end{bmatrix}
$$

1. Translation
	$(x', y') \to (x + a, y +b)$
	$A(2, 3) T (1,4) \to (3, 7)$
\
2. Reflection/mirror
	 X-axis -> (X, Y) -> (X, -Y)
	 Y-axis -> (X, Y) -> (-X, Y)
	 y = x -> (X, Y) -> (Y, X)
	 x = -y -> (X, Y) -> (-Y, -X)

3. Rotation
	90 -> (x, y) -> (-y, x)
	180 -> (x, y) -> (-x, -y)
	270 -> (x, y) -> (y, -x)
	360 -> (x, y) -> (x, y)

Formula:
$$
\begin{bmatrix}
x' \\
y'
\end{bmatrix}
=
\begin{bmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
$$

4. Dilatation
	Scale by 3
	$A(3, 5) .3 = A'(9,15)$ 