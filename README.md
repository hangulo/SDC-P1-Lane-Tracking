# **Project #1: Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

In this project, I built a computer vision pipeline to detect lanes lines using various image analysis and mathematical techniques.   The pipeline consists of:

1. Converting a single frame to grayscale
2. Creating a mask to detect areas in yellow and white color range
3. Applying a Gaussian Blur to smooth out image to have less noise for Canny Edge Detection
4. Running Canny Edge Detection
5. Applying a mask to ignore things outside of where we 'expect' to see lane lines
6. Running a Hough Transform to identify all the lines 
7. ** TO DO ** Extrapolate the average of the lines so we have only 1 line for each lane
8. Draw the lines we identified onto the original frame (in color red)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming is that my ROI definition is VERY specific and essentially 'hardcoded' with advance knowledge of the image size, camera placement, etc.  Even if I used the image shape variable defining static ROI for the region the lane is expected would not work for very curvy roads or big changes in elevation.  A smarter detection of the lanes (i.e vanishing point, curvature, etc) is necessary.

Another shortcoming will be more evident when there are more obstructions to the lanes (i.e heavy traffic, lane changes, shadows, barely visible or duplicate/old lane markings).


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to some smarter/dynamic detection of the right ROI that would support different camera placement or really just the lanes and horizon not being so centered.

Another potential improvement could be to better handle curved roads like in the challenge video.  The hough detection there currently goes very crazy so will need to be smarter about detection real lines and find a way to reduce the noise in pre-processing to get a better output.
