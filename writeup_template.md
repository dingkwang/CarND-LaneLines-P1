# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image0]: ./examples/grayscale.jpg "Grayscale"

[image1]: ./test_images/out_out_whiteCarLaneSwitch.jpg
[image2]: ./test_images/blur.png
[image3]: ./test_images/edge.png
[image4]: ./test_images/cropped.png
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I crop the region of interest from image based on observation. Then the image is coverted to gray scale using cv2.cvtColor(masked_img, cv2.COLOR_RGB2GRAY). Next, GaussianBlur with a kernel_size of 5 is used to supress the noise in the image. Next, canny edges detection is used to find the edges, and the threshold selection is [50, 150]. Then hough_lines is used to find the long and consisted lines as the road line. Finally the road line are overlapped with the image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by find the left/right line through comparing the slops then use polyfit to find the single line. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![blur][image2]
![edge][image3]
![cropper][image4]
![Final][image1]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the light is poor. As the noise increase, the failure of edge detection will increase. IR camera or LiDAR may be used as redundancy. 

Another shortcoming could be when the car ahead is too close to the ego car, and the road lines may be blocked or wrong lines may be detected. This can be solved by adding addition lower position cameras at the two sides of the car. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use IR camera to improve the night vision. 

Another potential improvement could be to add side view cameras to detect the roadline. 
