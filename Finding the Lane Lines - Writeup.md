# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. 

My pipeline consisted of the following steps:
    1- Create a grayscale copy of the image
    2- Applying Gaussian blur
    3- Finding edges using Canny method
    4- Creating a mask on the image to only process the region of interest
    5- Using hough line method to create lines connecting the points detected by canny finction
    6- Creating two single solid guide lines in order to show the lane lines. This step is further explained below.
    7- Imposing the processed image with line over the original image and plotting it

Step 6:
The idea is to divide slopes of hough_lines into positive and negative group. Then take an average over each group. Then assign positive averaged slope as slope of the left guide line and negative to the right line. By assuming each line equation to be y=mx+b, b is calculated by solving the line equation for b when passing throgh the mid point of the guideline. In order to calculate the midpoint, all Xs and Ys contributing in hough_lines are called and their midpoint is calculated as sum(all x)/(number of points). The same procedure is done formid point of y axis which is basically the midpoint between the upper edge of mask and bottom of the image.
Also draw line function was modified to be able to ignore no left or no right line in case no line is detected.



### 2. Shortcomings and resolution proposal


Unfortunately, I did not have time to work on the challenge project. I will be spending time to do it later. However, my initial idea is that by modifiying the vertices, this video can also be processed correctly.

Draw line function's code is too long and can be modified to be shorter and more efficient. This needs more time to modify the parameters and improve the loops.

Another item is that "draw lines" are not changing smoothly between frames. It means that the calculated slope, upper point, and lower point change largely frame to frame. I think this can be modified by defining a filter or smoothing changes between "only" two consecutive frames. However, if large changes persisted, code should allow the slope to change as it is calculated.

Another shortcoming is that in some frames, no line is being detected on the side with a dashed line. This can be easily resolved by optimizing the canny and hough line functions' parameters.


