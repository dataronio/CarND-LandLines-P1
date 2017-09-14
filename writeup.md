# **Finding Lane Lines on the Road** 

## Reflections on the Lane Finding Project


[//]: # (Image References)

[image1]: ./saved_images/graysolidYellowLeft.jpg "Grayscale"
[image2]: ./saved_images/blursolidYellowLeft.jpg "Blurred"
[image3]: ./saved_images/edgessolidYellowLeft.jpg "Canny Edges"
[image4]: ./saved_images/maskedsolidYellowLeft.jpg "Masked"
[image5]: ./saved_images/houghsolidYellowLeft.jpg "Hough"


## 1. The Lane Finding Pipeline.

### **Steps in the lane finding pipeline**

---

The following are the computer vision processing steps of the lane finding pipeline:
1. Convert input image to grayscale. 
2. Blur image with Gaussian kernel.
3. Apply Canny Edge Detector.
4. Mask the image to define the region of interest.
5. Apply Hough Transform and superimpose detected lane lines.

---

My pipeline consists of 5 steps. 

In the First step, input images are converted to grayscale.  This is necessary for the Canny Edge Detector to detect gradient changes that resolve to edges.

![alt text][image1]

The second step is to blur the grayscaled image using a Gaussian Blur kernel.  I choose a 5 x 5 kernel size.  This reduces anomalous edges due to noise in the image.

![alt text][image2]

The third step is to apply the Canny Edge Detector.  I have chosen 50 and 150 as the low and high threshold parameters.  This is in accordance with Canny's own guidelines of using between a 1:2 and 1:3 ratio for the threshold parameters.

![alt text][image3]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...


### 2. Potential shortcomings in the current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggestion for improvements in the pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
