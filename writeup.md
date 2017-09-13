### Finding Lane Lines on the Road

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My full, picture-processing pipeline has 9 possible steps, however the one used in the function for the video stream has only 6. Please note that all fine tunings were done manually and they may be subjective.

1. Read all images (only during picture-processing).
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/1_initial.jpg)
---

2. Use Gaussian blur in order to reduce the details on the picture and to make edge detection clearer later.
![alt text]()
---

3. Select the appropriate colors - white and yellow - for lane detection.
![alt text]()
---

4. Apply Canny edge detection to help finding the lanes' long edges.
![alt text]()
---

5. Select the region of interest.
![alt text]()
---

6. Calculate the Hough lines to find the lane markings.
![alt text]()
---

7/A. Calculate the weighted image using the markings and the original picture (7/A or 7/B).
![alt text]()
---

7/B. Using extrapolation the extension of the markings are also to be plotted. This is the modified draw_lines() function. I first classified the lines into left lane markings (slope < -0.3) or right lane markings (slope > 0.3)
![alt text]()
---

8. Save image (only during picture-processing).


### 2. Identify potential shortcomings with your current pipeline

My pipeline uses 1st order polynomial (i.e. linear) fit to calculate the extensions of the lines, hence it can manage only straight sections and slight corners.

Another issues may be other bright, longitudinal patterns on the road, which may also be detected, as lanes.

This simple realization works well only in case of excellent visibility.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher order polynomial fits for extrapolation.

Color selection might be better using HSV instead of RGB.
