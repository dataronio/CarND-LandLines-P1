# **Finding Lane Lines on the Road** 

## Reflections on the Lane Finding Project


[//]: # (Image References)

[image1]: ./saved_images/graysolidYellowLeft.jpg "Grayscale"
[image2]: ./saved_images/blursolidYellowLeft.jpg "Blurred"
[image3]: ./saved_images/edgessolidYellowLeft.jpg "Canny Edges"
[image4]: ./saved_images/maskedsolidYellowLeft.jpg "Masked"
[image5]: ./saved_images/outsolidYellowLeft.jpg "Hough Lanes"


### 1. The Lane Finding Pipeline.

**Steps in the lane finding pipeline**

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

---

The second step is to blur the grayscaled image using a Gaussian Blur kernel.  I chose a 5 x 5 kernel size.  This reduces anomalous edges due to noise in the image. The blurred image is below.

![alt text][image2]

---

The third step is to apply the Canny Edge Detector.  I have chosen 50 and 150 as the low and high threshold parameters.  This is in accordance with Canny's own guidelines of using between a 1:2 and 1:3 ratio for the threshold parameters.  The detected edges are in the image below.

![alt text][image3]

---

The fourth step is to mask the edge image in order to define the region of interest for lane detection.  The area in front of the vehicle up to a narrowing quadrilateral to roughly the
middle of the image is used as the mask.  I use 6 parameters to move the four points of the mask. Details can be found in the notebook.  Below we see the results of the masking.

![alt text][image4]

---

The Hough Transform is used to detect line segments from the masked Canny edges.  There are many parameters that can be modified and the details are better left to the notebook code.
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first separating the positive and negative sloped line segments from the Hough Transformed Canny Edge image. I then average the slopes and intercepts of each group after excluding vertical lines.  Using this information, I then drew the left and right lane line using the OpenCV line function from a y-coordinate at the bottom of the image up to a y-coordinate around the top of the region of interest.  We can see the results superimposed on the original image below.


![alt text][image5]

### 2. Potential shortcomings in the current pipeline


One shortcoming is the reliance on straight line detection in the Hough Transform.  A sharply turning road will have lanes that look curved rather than converging straight to the horizon.

Also, steep grades will force us to adaptively track an optimal region of interest.  Jitter develops in the videos as the pipeline works only on the video frame by frame.

Finally, cracks in the road surface cause spurious lanes to be detected.


### 3. Suggestions for improvement in the pipeline

A possible improvement would be to apply some form of deformable template in the Hough Transform in order to handle sharply curving roads.

A means of better optimizing the parameters of the pipeline using a greater variety of road styles and surfaces needs to be developed.  Robustness needs to be added to reject horizontal Hough lines that are detected in road cracks.

Some form of exponential moving average from frame to frame could be added to reduce jitter.

Another potential improvement could be to recode the pipeline in C++ for use in a realistic automotive embedded system.
