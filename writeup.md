### Finding Lane Lines on the Road - Reflection

My full, picture-processing pipeline has 9 possible steps, however the one used in the function for the video stream has only 6. Please note that all fine tunings were done manually and they may be subjective.

1. Read all images (only during picture-processing).
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/1_initial.jpg)
---

2. Use Gaussian blur in order to reduce the unnecessary details in the picture and to make edge detection clearer later.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/2_smooth.jpg)
---

3. Select the appropriate colors - white and yellow - for lane detection.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/3_color.jpg)
---

4. Apply Canny edge detection to help finding the lanes' long edges.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/4_canny.jpg)
---

5. Select the region of interest.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/5_masked.jpg)
---

6. Calculate the Hough lines to find the lane markings.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/6_hough.jpg)
---

7/A. Calculate the weighted image using the markings and the original picture.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/7_weighted.jpg)
---

7/B. Or: Using extrapolation the extension of the markings are also to be plotted. This is the modified draw_lines() function. I first classified the lines into left lane markings (slope < -0.3) or right lane markings (slope > 0.3), then all end points of all lines are stored separately for left and right. The last step is to fit a line on each side onto these points in the region of interest.
![alt text](https://github.com/szokezsolt/CarND-Project1/blob/master/pics/8_extrapolated.jpg)
---

8. Save image (only during picture-processing).


### 2. Identify potential shortcomings with your current pipeline

My pipeline uses 1st order polynomial (i.e. linear) fit to calculate the extensions of the lines, hence it can manage only straight sections and slight corners.

Another issues may be other bright, longitudinal patterns on the road, which may also be detected, as lanes.

This simple realization works well only in case of excellent visibility.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher order polynomial fits for extrapolation.

Color selection might be better using HSV instead of RGB.
