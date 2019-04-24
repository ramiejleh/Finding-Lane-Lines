# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/output_image.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used the gaussian blur to smooth down the image, then i set the thresholds for the canny edge detection and ran the function on the smoothed down gray image, then i set the vertices fo rmy region of interest after a lot of trying and tuning after that i used the hough lines function to detect the lines in my region of interest (of which i tuned the parameters with testing), lastly i used the weighted image function to layer the lines that are detected and drawn over the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first calculating the slopes of the lines then removing any lines with irrelevant slopes (reducing jittering) then separating the right and left lane lines by slope then using the polyfit method to average the lines and then drawing only two lines on the image

The result image:

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the camera changes position, the pipeline is depending that the camera is always where it is in the video that are tested.

Another shortcoming could be when the car is making a turn the lanes might go outside of the region of interst in which case the pipeline would fail to detect it.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make a more complex polygon that might detect curves better in the video instead of just straight lanes.

Another potential improvement could be to have a more fine tuned algorithem to handle shadows better. shadows causes a problem in detecting edges because the gradient becomes weaker.
