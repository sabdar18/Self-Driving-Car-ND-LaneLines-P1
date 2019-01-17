# **Self Driving Car NanoDegree Project 1 : Finding Lane Lines on the Road** 

## Writeup Template **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflection of my work  in a written report


[//]: # (Image References)

[image1]: ./test_images_output/finalsolidWhiteCurve.jpg "Final Solid White Curve"
[image2]: ./test_images_output/finalsolidWhiteRight.jpg "Final Solid White Right"
[image3]: ./test_images_output/finalsolidYellowCurve.jpg "Final Solid Yellow Curve"
[image4]: ./test_images_output/finalsolidYellowCurve2.jpg "Final Solid Yellow Curve 2"

[image5]: ./test_images_output/finalsolidYellowLeft.jpg "Final Solid Yellow Left"
[image6]: ./test_images_output/finalwhiteCarLaneSwitch.jpg "Final White Car Lane Switch"

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
![alt text][image5]
![alt text][image6]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking points of x1,y1,x2,y2 and calculating slope m using the above points then based on slope i find to draw the line to left or right 

Here i am  taking one more helper function draw_line() to a draw line.

This function will take array of points x, y and based on the value of x array length it will draw a line otherwise it will return.

In this function , i am using np.polyfit with x, y points and drawing a single line by calculating m and b values finally drawing line using cv2.line() function




### 2. Identify potential shortcomings with your current pipeline


Then potential shortcoming would be 
1) The Lines drawn will be shaking in the video
2) For challenge video, the entire output will be different , it not able to detect lines properly 



### 3. Suggest possible improvements to your pipeline

The possible improvement would be 
1) Improve line drawing so that line shaking in the video is eliminated.
2) Need to improve to find lanes in challenge video scenario also
3) Need to improve the area to find the lanes 



