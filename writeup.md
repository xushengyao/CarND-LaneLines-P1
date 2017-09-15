# **Finding Lane Lines on the Road**

## Writeup

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)
[image1]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"

---

### Reflection

### 1. Describe your pipeline.

My pipeline function consisted of 5 steps.

* Converted the images to grayscale.
* Applied a Gaussian filter to smooth the image.
* Used a Canny Edge Detection to find the edges.
* Used region of interest function to select region inside the preset area.
* Used a Hough transformation to detect the lines on edge detected image.

Also, regarding the draw_lines( ) function, in order to get the full extent for both left and right lanes, some modifications have been done. Firstly, I need to find out useful left line and right line points according to the slope value. After that, a polynomial curve fitting function: polyfit has been used to fit the left and right line and we get two parameters for the fitted linear function (y=Ax+B). Using two parameters, we could get the top points and bottom points for left and right lanes and then draw both of them.

After using the new draw_lines function, I am able to get solid left and right lane lines. One example of the processed images is shown below:

![alt text][image1]


### 2. Potential shortcomings with current pipeline


I tried a lot to tune the parameters to make the pipeline more robust. While, there are still some drawbacks with the current implementation.
* The lines are not always smooth.
* The current implementation for draw_lines function can only handle the straight lane lines due to the first order curve fitting, and it will be failed in the curve lane case.
* The static region of interest is not very robust.


### 3. Possible improvements

Some possible improvements include:
* Trying more to tune the input parameters.
* Apply different curve fitting functions for different lane shape.
* Design a dynamic region of interest to handle multiple scenarios.
