Rafael Zefanya Jaya Surya
Z125075

Image scanning by devices are done pixel by pixel. For example, for greyscale images, it will scan pixel by pixel for each row and column, and each pixel is detected either bright or dark. Then, an analog wave is made for each row or scan line, the value of the wave is determined by how dark or light each pixel in the row is.

![[Pasted image 20250528173816.png]]

We then sample the data from the wave, and do discritizing, which then we will arrange the data to a grid. The data in each grid will have values from 0-255, with value 0 being dark and value 255 being bright. These numbers are stored in an array.

Now, for color images data, the process is a bit more thorough. We use several components like micro lens that collects the light, color filter that filters out Red, Green, Or blue, which will then get processed. The resulting processed data will have three total grids of image data, one for green, one for red, and one for blue, each representing different layers of the image, with this, we are able to capture the colors of an image data, by combining the three values of red, green, and blue from each layer, for each pixel.

In image processing, we use coordinate systems, and usually there are two methods,

![[Pasted image 20250528174227.png]]

This is often used for geometrical analysis while this,

![[Pasted image 20250528174244.png]]

Is used for programming.

From the coordinate system, we can do geometric transformations such as scaling, inverse transform of scaling, moving the coordinate, inverse transform of moving, and rotating as well as the inverse transform counterpart. This allows us to manipulate images.
