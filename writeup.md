# **Finding Lane Lines on the Road** 


### **Steps in the lane finding pipeline**

---

The following are the computer vision processing steps of the lane finding pipeline:
1. Convert input image to grayscale. 
2. Blur image with Gaussian kernel.
3. Apply Canny Edge Detector.
4. Mask the image to define the region of interest.
5. Apply Hough Transform and superimpose detected lane lines.



[//]: # (Image References)

[image1]: ./saved_images/graysolidYellowLeft.jpg "Grayscale"
[image2]: ./saved_images/blursolidYellowLeft.jpg "Blurred"
[image3]: ./saved_images/edgessolidYellowLeft.jpg "Canny Edges"
[image4]: ./saved_images/maskedsolidYellowLeft.jpg "Masked"
[image5]: ./saved_images/houghsolidYellowLeft.jpg "Hough"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
