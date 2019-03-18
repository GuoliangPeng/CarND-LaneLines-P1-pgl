# **Finding Lane Lines on the Road** 


---

**Finding Lane
Lines on the Road**
The goals / steps of this project are the following:
* Make
a pipeline that
finds lane lines on the road
* Reflect on my work in a written
report






---
###
Reflection

### 1. Describe your pipeline. As part of the
description,
explain
how you modified the draw_lines() function.

My pipeline
consisted of 5
steps.
First, I converted the images to grayscale, then I ....
In order to draw
a
single line on the left and right lanes, I modified the
draw_lines() function
by
...

If you'd like to include images to show how the
pipeline works, here is
how
to include an image: 

我的管道包括5个步骤：

1.我将原始三通道图像转换成单通道灰度图像：
![gray_image](./writeup_images/gray_image.png)
2.将灰度图像进行高斯滤波处理,使用canny算法检测图像中的边缘信息
![edges_image](./writeup_images/edges_image.png)
3.在感兴趣区域内通过霍夫变换对边缘点提取直线线段信息，标记出车道线
![line_edges1_image](./writeup_images/line_edges1_image.png)
4.将标记出的车道线叠加到原始图像中
![line1_image](./writeup_images/line1_image.png)
5.改进第3步标记车道线函数，对检测到的车道线进行平均和外推，用整条实线标记出完整车道线并叠加到原始图像中
![line_edges2_image](./writeup_images/line_edges2_image.png)
![line2_image](./writeup_images/line2_image.png)

### 2. Identify potential
shortcomings with
my current pipeline
一个潜在的缺点是在第5步中，使用最小二乘法拟合直线时在solidYellowLeft.mp4视频中有两帧图像拟合不准确，所以只能通过限制最小斜率范围达到准确识别效果。
另一个缺点是此检测和拟合算法在相机颠簸的情况下拟合出来的直线左右抖动明显。

此算法不适用于弯道车道线标记。


### 3. Suggest
possible
improvements to my pipeline

一个可能的改进方式是：以线段的长度做加权平均来替代最小二乘法拟合直线
或者用其他方法来检测并拟合车道线
