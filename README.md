# **Project #1: Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

In this project, I built a computer vision pipeline to detect lanes lines using various image analysis and mathematical techniques.   The pipeline consists of:

1. Converting a single frame to grayscale
2. Creating a mask to detect areas in yellow and white color range
3. Applying a Gaussian Blur to smooth out image to have less noise for Canny Edge Detection
4. Running Canny Edge Detection
5. Applying a mask to ignore things outside of where we 'expect' to see lane lines
6. Running a Hough Transform to identify all the lines 
7. ** TO DO ** Modified the Draw_lines function to extrapolate the average of the lines so we have only 1 line for each lane
8. Draw the lines we identified onto the original frame (in color red)


###  Shortcomings / Areas for improvement of current Pipeline and potential areas of 


One potential shortcoming is that my ROI definition is VERY specific and essentially 'hardcoded' with advance knowledge of the image size, camera placement, etc.  Even if I used 'image.shape' values to better define a static  ROI for the region the lane is expected, it still would not work for big changes in elevation.  A smarter detection of the lanes (i.e vanishing point, curvature, etc) is necessary where it doesnt depend on lane lines and horizon always being centered.

Another shortcoming will be more evident when there are more obstructions to the lanes (i.e heavy traffic, lane changes, shadows, barely visible or duplicate/old lane markings) or the lanes being very curvy since it wreaks havoc to my current pipeline.  Will need to be smarter in pre-processing so there isnt so many possible data points for lines sent to the Hough Transform function.

