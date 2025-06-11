Rafael Zefanya Jaya Surya
Z125075

# Edge detections

**8 Neighborhood pixels**
Surrounding 8 pixels of a central pixel is called 8 neighborhood pixel.

**Connected component**
Group of pixels that have the same value and connected to each other

## Contour

We can detect edges of an image by analyzing the contours. For example, the edge of a part of an image will have a jump in value from one pixel to it's adjacent pixel.

![[image-23.png|553x303]]

It also applies to line shapes that's combined by two edges.

![[image-24.png|557x378]]

While gradients have changes in brightness, it's not considered an edge because no steps in brightness, change is a curve.

We can extract only the edges of an image by exploiting the step in brightness of pixels. First differential -> Gradient, Second differential -> Laplacian.
To extract the contour, we need to pick up the "peak" of the contour, or the zero point of laplacian.

We can extract gradients using these formulas:
Differential of x orientation : $f_{x}=f(x+1,y)-f(x,y)$
Differential of y orientation: $f_{y}=f(x,y+1)-f(x,y)$
Magnitude of vector: $\sqrt{ f_{x}^{2}+f_{y}^2 }$

![[image-25.png|578x400]]

