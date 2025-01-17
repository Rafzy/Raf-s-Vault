# Essay

1. Pre-processing is an important step not only in computer vision, but in most fields in AI. There are several reasons why we do pre-processing, either to enhance the input's image quality, emphasize on key features of the image, or standardizing the image inputs needed to train the model.
   Whatever the techniques used is, in general, preprocessing is a step to prepare the input data to train the model, making it easier for the model to extract features from the input images, and possibly improving the model's performance
   There are several techniques that are available in pre-processing computer vision input data
	- Resizing
     If the training data images varies greatly throughout the images and cause the model to not identify some of the key features, we may want to resize them to a standard size or resolution, we do this so that the size of the image won't focus too much on the size of the image, rather the important features.
     On the other hand, if the model seems to overfit, we may want to resize some of the images so that they vary a bit, and the model can generalize the input features better, making it perform better in predicting the unseen data.

	- Normalization
	  With numerical values, normalization includes "normalizing" those values so they fit a standard range (0 to 1, -1 to 1). In computer vision and with images, normalizing means standardizing each pixel values to a standard range
	  We do this to make the input images uniform in terms of pixel brightness, so that the model won't focus on the different brightness of the picture, rather can extract actual meaningful information
	  But again we do this depending on how the model performs, if the model overfits and cannot generalize the features, we may want to add some noise to the training images to introduce a bit of randomness so the model can handle unseen data.

	- Augmentation
	  Augmentation means expanding the number of dataset you have by creating copies of existing images, and modifying them, like rotating them, change their colors, etc.
	  We do this to reduce the chance of the model overfitting, so the model can generalize the features of the training images, despite of the different angles, color, lighting, saturation, etc.


2. Both box filter and median filter are techniques where we use a mask (matrix of `N x N` size) and run over those mask across the image and convolute the image (A part of convolution technique). We do this to smoothen out the image, and reduce noise to prepare the input data for image processing.
   
   **Box Filter**
   Box plot works by going around each pixel, and averaging out that pixel based on it's neighboring pixels (Usually a rectangular or a box, and the size depends on the kernel used).
   We use a kernel of varying size depending on what we need and want, and the kernel contains the same weight for each cell (usually 1). And we run over the kernel to the image, and replacing each pixel's value to the average of the pixel values that's covered by the kernel.
   Doing this will smoothen out the image, but because of the nature of averaging the pixels, using this method can cause the image to lose it's features like edges and corners.
   
   **Median Filter**
   Median filter uses a kernel similar to median filter, but instead of averaging out the pixel values inside of the kernel, we replace the pixel value with the median of all the pixels. Doing this will reduce the noise same with the box filter, but it can still maintain important features such as edges and corners. This method is effective at reducing "salt and pepper" noise (It's the noise similar to how a tv's white noise, containing white and black pixels all over the image).
   
   In terms of which method is preferred, typically it depends on the use case, if we want a stronger smoothing effect, we may use boxplot because of it's use of averaging the pixels, but if we want to retain important features we may want to use median filter.
   
   In general though i would guess that median filter is typically preferred because of it's ability to retain features while smoothing out the image.

$$
\begin{bmatrix}
203 & 104 & 209 & 74 & 33 \\
139 & 4 & 31 & 66 & 169 \\
246 & 100 & 33 & 159 & 195 \\
177 & 31 & 212 & 176 & 239 \\
79 & 42 & 155 & 237 & 175 
\end{bmatrix}
$$

## Box Filter Method 1:

For the first method, i will use a kernel that covers the whole image, (5x5 kernel), and assume that edges and corner will be zero.

$\frac{203 + 104 + 209 + 74 + 33 + 139 + 4 + 31 + 66 + 169 + 246 + 100 + 33 + 159 + 195 + 177 + 31 + 212 + 176 + 239 + 79 + 42 + 155 + 237 + 175}{25}= 131.52$

## Box Filter Method 2:

We will use a 3x3 kernel:
$$
\begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$

Result of Box Filter
(Note: This is assuming for the kernel in the edges and the corner, i calculate the average only for four values in the corner, and six values for the edges when i run the kernel over them so i don't assume 0 for edges or corners like some other variations of box filtering techniques.)
$$
\begin{bmatrix}
112.5 & 115 & 81.3  & 97 & 85.5 \\
132.7 & 118.8 & 86.7  & 107.7 & 116 \\
116.2 & 108.2 & 90.2 & 142.2 & 167.3 \\
112.5 & 119.4 & 127.2 & 175.7 & 196.8 \\
82.25 & 116 & 142.1 & 199  & 206.7
\end{bmatrix}
$$
Explanation: By running over the 3x3 matrix over the matrix, i calculate the average of each pixel that's covered by the matrix, and replace the pixel value in the middle with the average of the pixels around it.

## Method 1 Median Filter

For this method, i will assume a kernel that covers the whole matrix, and find the median based on this kernel:
$median(203 , 104 , 209 , 74 , 33 , 139 , 4 , 31 , 66 , 169 , 246 , 100 , 33 , 159 , 195 , 177 , 31 , 212 , 176 , 239 , 79 , 42 , 155 , 237 ,175) = 155$
(Note: Before finding the median, the numbers are sorted first)



3. Selected algorithm : SIFT (Scale-Invariant Feature Transform)
   SIFT works by adding multiple layers of gaussian filters, and it's supposed to represent how the image looks from different "distances". The algorithm will then subtract each blurred image to get what's called the Difference of Gaussians, this will essentially preserve spatial information that's contained between the two blurred images
   So these are the steps for SIFT algorithm to do feature extraction:
   1. Blurs the image multiple times, saving each layer of blurring
   2. Calculates difference of gaussian by subtracting each blurred image from the other, this will then highlight parts of the image with rapid change in the pixel value, and it's more likely to be either edges or corners
   3. The algorithm will then go through each pixel in the image, and compare it with the adjacent pixels
   4. If that pixel selected is a local maximum or minimum, it's marked as a potential key point
   5. After getting all the potential key points marked, the algorithm will use Taylor serios expansion to localize each key point in a more precise manner 
   6. Now, for each refined key points, the algorithm will generate a descriptor in a form of vectors. This descriptor will be the thing the algorithm uses to compare it to other key points in other images

   The best types of features that's suitable for SIFT algorithm to extract are local features, that doesn't change too much under various transformations. Meaning, SIFT algorithm can detect images with various sizes, rotations, scale, or gradient transformation between images, because local features don't really change much with those types of transformations.
   And because SIFT uses the Difference of Gaussian method, which is really good at detecting edges and corners, SIFT is good at identifying those particular parts of an image, and marking them as keypoints of an image.
   
   There are several advantages to using SIFT algorithm, like detecting features like mentioned before, features at various sizes, scale, rotation, etc, because SIFT algorithm excels at extracting those types of features. But because SIFT works by layering gaussian blur to compute the DoG, it can be pretty computationally more demanding and also consumes more memory when executing compared to other techniques.


# Case

1. a. The python code is provided with the zip file under `number1.py`
   b. `equalizeHist` works by redistributing the pixel values of an image by transforming the histogram of pixel intensity of the image. This will create a uniform distribution of intensities throughout the input image, and it kind of stretches out the intensity range of the image, meaning dark areas will look darker and bright areas look brighter
   This is the reason why applying `equalizeHist` to an image make the image appear sharper. And applying this to a low contrast image can help it regain better quality, suitable for processing.
   Some changes i noticed in the output image after running it through the code, some features become less prominent after running through `equalizeHist`, like some edges or corners that is a bit subtle, for example edges or corners in a dark area, make it seem harder to spot after the preprocessing. This may be due to the intensity being uniform across the image, so subtle features like that become less prominent.

2. a. The python code is provided with the zip file under `number2.py`
   Explanation:
   From the output of my code for edge detection, the canny image seems more precise and clear on the edges it detects, meanwhile sobel is able to detect the "smoother" edges, even edges that isn't as prominent like edges in the background.
   Canny precisely predicted the prominent edges, meanwhile sobel detects the less prominent edges though not as clear as canny.
   This might be explained by the way canny and sobel works in edge detection. Sobel method utilizes two 3x3 kernel to convolute the image, one of the kernel will detect vertical changes (changes in values, so edges detected vertically) and the other for horizontal changes. This approach is more direct and sobel doesn't alter or transform the image in any way.
   Meanwhile, canny method includes many steps to detect edges, canny will first use gaussian blur first, it will then calculate the gradient magnitude and direction, it will then thin out and smoothens out the edges by taking the maximum value for an area, it will then exact a high and low threshold to identify weaker and stronger edges, and it will then connect weaker edges to stronger edges, and removing weaker edges that cannot connect.
   
   Steps like the gaussian blur and edge tracking might explain why the canny method is more precise and exact, canny method only predicts the "stronger" or more prominent edges, which explains why the canny method doesn't detect any edges of the background image, because the algorithm may deem them as "weak edges", meanwhile sobel method simply runs two 3x3 kernels to the image, which will reveal any edges it detects despite it being weak or strong.

3. The python code is provided with the zip file under `number3.py`