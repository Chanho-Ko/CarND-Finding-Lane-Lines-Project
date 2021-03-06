# **Finding Lane Lines on the Road** 
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Apply a pipeline for the video
* Modify the draw_lines() function for creating a single line of right and left lane


[//]: # (Image References)

[image_in]: ./test_images/solidWhiteRight.jpg "Input image"
[image_out]: ./test_images_output/solidWhiteRight.jpg "Output image"

---

## Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project, it will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

### 1. Description of pipeline.

My pipeline consisted of 5 steps. 
* Input image is converted into gray scale image, and filtered with Gaussian smoothing.
* Detection canny edges with proper low and high thresholds.
* Masked edge image is created baseed on four vertices that we are interested in.
* Creating line image that includes all of lines calculated by Hough transform.
* Draw a single line on the left and right lanes by averaging and extrapolation.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function.
The left and right line is decided by the sign of slope of the line.
x and y points are sumed up and the average of points and slope are calulated.
Based on the point and slope, the line is exprapolated based on the range of y coordinate.

The result for a example image is shown below:

![alt text][image_out]

Red lines are the created lane lines by my pipeline. Please refer to the Jupyter file for details of description and python codes.

### 2. Suggest possible improvements to my pipeline

A fluctuating effect is often detected in the result video. It can be improved by fine tunning. However, the tunning parameters can be differ on another evironments.
Changing parameters adaptively with deep learning model can be possible improvements.
