#computervision 

# Digital image transformation

Typically in images, every pixel or point will contain a matrix with values between 0-255. Typically this value indicates the value for each color of RGB. The higher the value, the more of that specific color appears. 

# Image Processing

Image processing is the process of manipulating and analyzing an image to extract meaningful information and make them useful for various tasks.

Types of image processing operations:
- Original image?
- Increased contrast
- Change in hue
- Posterized
- Blurred
- Rotated

## Color stretching

Also known as contrast stretching or color normalization, a type of image processing where we modify the contrast or hue of an image by modifying the range of color and intensity values.

## How it works

we transform the pixel values of an input image so that the color are spread over the full range. For example, a pixel value of 50-150 in a 0-255 scale is stretched to span the full range of 0-255 can make color variations more noticeable.

![[Pasted image 20240919155612.png]]

The R and S represents "How much" we shift the color intensity. R and S will be given.

we can use this formula to determine $\alpha$, $\beta$, $\gamma$

$$
m = \frac{y_{2} - y_{1}}{(x_{2} - x_{1})}
$$

# Logarithmic Transformation

Logarithmic transformation is another technique in image processing where we increase the contrast of an image. This technique is effective in compressing dynamic range, highlighting details darker regions, and suppressing the dominance of brighter regions 

$g(x, y) = C.\log(1 + f(x, y))$

C -> constant value


# Image Filtering

Two types of filtering:
- Linear filtering:
	- Box filter
	- Weight average
	- Gaussian filter
- Non-linear filtering:
	- Median filter
	- min filter
	- max filter


Filtering uses smooth spatial -> Used to perform blurring and noise reduction

