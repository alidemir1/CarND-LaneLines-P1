# **Finding Lane Lines on the Road** 


---

[//]: # (Image References)

[image1]: ./test_images_output/0.png "Hough Lines"
[image2]: ./test_images_output/result.png "Average Lines"

---


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted following steps; 

* Color transform is applied from RGB to Gray
* Smoother picture is gathered via Gaussian Blur
* Edges are obtained with canny edge algorithm
* Hough transform is applied on ROI
* Weighted image is calculated for visualization purposes.

After applying above steps, it is observed more than one  lines are detected on each of both left and right sides. 

![alt text][image1]

In order to obtain single line on each both sides; draw_lines() function is modified. Side of the lines are detected by their slope. All the lines in left and right are clustered and average of each cluster is calculated. Average lines are obtained for both left and right clusters.

![alt text][image2]



### 2. Identify potential shortcomings with your current pipeline
Current pipeline is too dependent on the size and location of the lane lines, in different placement of the camera this might be a problem. 

Another thing is that in case of noisy road conditions such as shadows in the ROI or some cracks on the road might create noise for canny edge detection which might cause erroneous calculation of average lines.


### 3. Suggest possible improvements to your pipeline

Instead of depending on triangular ROI, sequential small ROIs can be used starting from bottom of the image to top side.
