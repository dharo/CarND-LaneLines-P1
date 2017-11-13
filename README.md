
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
[night_gif]: ./test_videos_output/night.gif "Night"

---

### Reflection

### 1. The pipeline: meat and bones of locating lane lines from images

This consists of 5 main steps :
![gray]

    1. Grayscale: Taking colors out of the image to begin filtering out the data needed to identify
    objects of interest -- in this case lane lines.
    

![blur]

    2. Gaussian Blur: Blurring the image is required to filter out any noise from less prominent edges.
[OpenCV GaussianBlur](https://docs.opencv.org/2.4/modules/imgproc/doc/filtering.html?highlight=gaussianblur#gaussianblur)

![canny]

    3. Canny Algorithm: Grayscaled image is put through a Canny algorithm
    to identify edges in an image.
[OpenCV Canny Edge Detector](https://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/canny_detector/canny_detector.html#canny-edge-detector)    

![roi]

    4. Focus on region of interest: Focus on region of interest. 
    We know that lane lines are located on a specigic region on the image.
    We remove all else in order to find the lines that make up the lane.




![hough] ![result]

    5. Hough and annotating original image: Hough algorithm takes the Canny
    and region reduced image to locate lines. Finally lines are identified 
    and average points are calculated to draw the lines on the original image
[OpenCV Hough Line Transform](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_imgproc/py_houghlines/py_houghlines.html#hough-line-transform)

---

### 2. Identify potential shortcomings with your current pipeline

There exists some situations where the current solution will fail to locate lines. 
These situations include worn down lines on a road, multiple lanelines such as carpool lane in night.mp4
The current implementation of the pipeline is designed around daytime drives and single lined lane markers.

This pipeline is also assuming the horizon (road meets sky) is under the center of the frame by about 5% of the frame height.
This value would have to be calibrated depending on the way a camera is mounted and how much of the lane we want to see.

---

### 3. Suggest possible improvements to your pipeline

The biggest improvement this pipeline can use is removing the jitter introduced between frames. 
This jitter is caused by the constant calculation of lines on individual frames. This could be addressed
by keeping a running average of drawn Hough lines from the previous frame and included into the calculation
of the current frame's Hough lines.

---

### Pipeline tested with night driving

Values for tuning image algorithms were left unchaged.

![night_gif]
