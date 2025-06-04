Rafael Zefanya Jaya Surya
Z125075

**Binarization**
We can imagine an input image, with bright pixels as the object, and dark pixels for the background. 
![[image-18.png|419x257]]

Each pixel has coordinates, and values like discussed in the last session, ranging from \[0-255] stored as arrays. For this case, the pixels where the object would be would have high value, while the dark image would have lower values.
Binarization is the process of converting those values into purely (0, 1), based on a threshold put against each of the pixels.
This is the formula:
![[image-19.png|438x128]]

So, in the case of the object in the image, we can get this type of value if we put a certain threshold .
![[image-20.png|414x311]]

Where the pixels with value 1 indicates where the object may be while the background is 0. With this, we can also find the center of gravity. 

First we need to find what's called as the "moment" of the image with this equation.
![[image-21.png|505x111]]

and we use this equation to calculate the center of gravity of the image.
![[image-22.png|527x169]]


**8 Neighboring pixels**
From the central pixel, if there are 8 surrounding pixels with value of 1, then they are called 8 neighboring pixels. 

Connected component -> groups of pixels that have the same value connected to each other.

Usually when we do binarization, there can be a lot of noise (pixels with value of 1 scattered across the image). we can solve this with several methods

One of them is called "moving average method". we calculate the value of the center pixel by averaging it with it's 8 neighboring pixels, however, doing this can make the image blurry.

Other than that, we can also use "median filter", where instead of finding the average, we replace the center pixel with the median of that pixel with it's 8 neighboring pixels. with this, it can result in a clearer output compared to the moving average method.