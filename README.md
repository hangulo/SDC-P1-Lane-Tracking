# **Project #1: Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./test_images/pipeline.png "Pipeline"

---

### Reflection

In this project, I built a computer vision pipeline to detect lanes lines using various image analysis and mathematical techniques.   The pipeline takes in a single frame and then:

1. Converts the image to grayscale (to 'flatten' the image to 1 channel vs the 3 channels it's normally in)
2. Creates a mask to detect areas in yellow and white color range 
3. Applies a Gaussian Blur to smooth out image to have less noise for Canny Edge Detection
4. Runs Canny Edge Detection (labeled as "Canny Edge" below)
5. Applies a mask to ignore things outside of where we 'expect' to see lane lines (labeled as "ROI" below)
6. Runs a Hough Transform to identify all the potential lines found in the image (labeled as "Hough Lines" below)
7. Groups all the lines into potential 'left' and 'right' lane lines, removes any unlikely lane lines (i.e horizontal or vertical lines) and then draws a single lane line using the average slope and expected extremes of each line.
8. Finally, draw the 2 lane lines we identified onto the original frame (labeled as "Final" below)

![alt text][image1]

###  Shortcomings / Areas for improvement in current pipeline 


My ROI definition is VERY specific and essentially 'hardcoded' with advance knowledge of the image size, camera placement, etc.  Even if I used 'image.shape' values to better define a static  ROI for the region the lane is expected, it still would not work for big changes in elevation.  A smarter detection of the lanes (i.e vanishing point, curvature, etc) is necessary where it doesnt depend on lane lines and horizon always being centered.

Another shortcoming will be more evident when there are more obstructions to the lanes (i.e heavy traffic, lane changes, shadows, barely visible or duplicate/old lane markings) or the lanes being very curvy since it wreaks havoc to my current pipeline.  Will need to be smarter in pre-processing so there aren't so many possible data points for lines sent to the Hough Transform function.

Lastly, the ines could be smoother (they flicker a bit near bottom like the example p1 video).  If I were to add caching or memory to smooth out between frames that will help greatly.