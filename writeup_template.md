# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used Gaussian blurring and Canny transform to detect edges. Then I created a masked edges image by defining a four sided polygon. Then I detected straight lines with Hough transform. Finally I drew lines on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the average of the slope and intercept of the lines weighed by their lengths. Then I calculated the x positions based on the y positions of top and bottom of the lanes. Finally, I drew two thick lines. 




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lanes right ahead are curved. Based on the results from the challenging video, the current pipeline failed to detect lanes from such videos.

Another shortcoming could be the lines couldn't transition from frame to frame smoothly. Also, the current pipeline don't detect line from nearby lanes, so the car couldn't switch lanes.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to include lines from previous frame into the calculation of the average line from the current frame.

Another potential improvement could be to optimize the Hough transform to allow the detection of curved lanes. Increase the size of the mask will allow detection of lines from other lanes but it will be more computationally expensive.
