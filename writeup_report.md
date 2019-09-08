**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg

### Reflection

### 1. Describe your pipeline. 

My pipeline consisted of 6 steps as mentioned below. 
1. Convert the image to grayscale
2. Apply gaussian blur with kernel_size of 3
3. Get the canny edge detections
4. Define Region of interest and get the masked output
5. Apply hough transform and get the lines inside the ROI
6. Interpolate and approximate the lines to draw the entire lane lines

In order to draw a single line on the left and right lanes, I gathered all the co-ordinates of the line segments and fit 2 lines for the left lane and right lane. I observed that there are a few outliers (like a small negative slope line segments on the left line which had to be positive) and this was throwing the fit line off. I added if conditions to only append the correct coordinates to the respective co-ordinates arrays. I then calculated the intersection points of this fit line with the ROI horizontal edges and drew the lane lines

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be when there is a car quite close to the lane lines. I did try the pipeline on the challenge too. While I could get a fair amount of lines on the road even with a lot of distractions, I could not filter out the edges when a car is quite close to the lane lines and also when there is a bridge section with a whiter road color. I did see that the front camera sees a part of the front section of the car and I changed my ROI accordingly. Also I changed the xsize and ysize to be relative to the image size instead of declared constants. 

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make the edge detections and line fitting more robust. As can be seen in one of the videos where there is a yellow line on the left, some of the edges from the curb are also creeping and throwing the lane line fit off. I will work on this as I get more experience with python and the math involved.
