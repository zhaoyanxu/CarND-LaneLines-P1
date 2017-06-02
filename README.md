# **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./example.png "Detection Result Demonstration"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I define a interest regsion as [(100,600), (500,300), (500,300),(900,600)] for gaussian blurring.
Next, I applied the canny edge detection and set the threshold as [50, 150]. After that, I apply hough line detection algo and extract the regsion of interest as [(100,550), (40,322), (530,322),(950,550)].
Lastly, I apply weighted image to get the result.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by defining the slope of left and right line.
Through examining the slope of each node, I first determine which line, left or right, each node belongs, and then adjust the line by averaging the node location.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the line is out of my predefined interest region.

Another shortcoming could be if a car, like a lone truck is close to my view. It may detect it as lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to dynamically adjust the region of interest by object detection.
