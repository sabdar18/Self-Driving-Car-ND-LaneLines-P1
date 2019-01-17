# **Self Driving Car NanoDegree Project 1 : Finding Lane Lines on the Road** 

## Writeup Template **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/finalSolidWhiteCurve.jpg "Final Solid White Curve"
[image2]: ./test_images_output/finalSolidWhiteRight.jpg "Final Solid White Right"
[image3]: ./test_images_output/finalSolidYellowCurve.jpg "Final Solid Yellow Curve"
[image4]: ./test_images_output/finalSolidWhiteCurve2.jpg "Final Solid Yellow Curve 2"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My Pipeline consists of following steps:
1) take the image using the function name lane_finding_pipeline() 
2) Convert the image to grayscale using helper function grayscale which returns image from cv2.cvtColor() function
3) Apply gaussian blur to the the grayscale image using gaussian_blur() function which using cv2.GaussianBlur() function and kernel_size 
4) pass the blur image to canny() function with low_threshold and high_threshold values
5) Then create masked image using  the region_of_interest() pass some vertices  so that it will select the area formed by the vertices, it uses cv2.fillPoly() function 
6) pass the masked image to hough_lines() function which uses cv2.HoughLinesP() and also some input parameters to give output of the desired image
7) with in the hough_lines() function we will draw the lines on the image , this will explain in detail below
8) finally pass the output from hough_lines() to weighted_img() function with initial image , to combine and get the ouput of images as follows: 

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

<!-- ![alt text][image1] -->


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
