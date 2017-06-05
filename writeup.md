# **Finding Lane Lines on the Road**

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:
- Convert the images to grayscale
- Run a gaussian blur on the image
- Use Canny edge detection to find edges
- Mask the pixels that were part of edges outside of the area of interest
- Use Hough transform to find lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by excluding lines that have an angle less that 15 degrees from the x axis. I sorted the lines by the sign of the slope. If it is positive, the line belongs to the right divider line. Else, it was part of the left divider line. For both left and right divider lines, I averaged the position of the lines. I used one of the endpoints and the formula of the slope to extrapolate the X position of the endpoints at the bottom and top of the lane.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming is when there is low contrast between the lane marker and the road. This is the case in the challenge video when the yellow lane marker is in the shadows or on the concrete surface of the bridge. Many roads in North America have faded lane markings. The pipeline would also struggle with reflections from the road surface when it is raining.

The pipeline would not perform well with tight curves in the roadway.

Another issue would be varying road surfaces where potholes or other defects have been patched. These edges and lines would likely be detected by this pipeline.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use color selection for both the yellow and white lane markings.
