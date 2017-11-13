
# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />


David Haro - November 2017

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[gold]: ./result_images/gold.png "Gold"
[gray]: ./result_images/grayscaled.png "Gray"
[blur]: ./result_images/Gaussian_blur.png "Blur"
[canny]: ./result_images/Canny.png "Canny"
[roi]: ./result_images/Region_of_interest.png "roi"
[hough]: ./result_images/Hough.png "Hough"
[result]: ./result_images/Result.png "Result"

---

### Reflection

### 1. The pipeline: meat and bones of locating lane lines from images

This consists of A FEW STEPS:
1. Grayscale: 

![alt text][gray]

    Taking colors out of the image to begin filtering out the data needed to identify
    objects of interest -- in this case lane lines.
2. Gaussian Blur:
    Blurring the image is required to filter out any noise from less prominent edges in the image.
3. Canny Algorithm:
    
4. Focus on region of interest
5. Hough and annotating original image
 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
