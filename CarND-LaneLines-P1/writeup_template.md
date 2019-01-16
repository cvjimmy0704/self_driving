# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I wrapped up the method draw_lines() in another method draw_solid_line(). The main idea is that I first used the slopes to determine a given line segment is on the left lines set or right lines set. For each of these sets, I sorted  the lines in that set along the x axis of the first point. Then travel through the set, connect end points of a line and the start point of the next line. If the connecting segment has the correct slope as the set (positive for left set and negative for right set), then I add the connecting segment into the set. Else just ignore. For example, if two lines (x1, y1, x2, y2) and (a1, b1, a2, b2) are in the left lines set. We check if the connecting segment (x2, y2, a1, b1) has positive slope then do or do not add into the set accordingly.


### 2. Identify potential shortcomings with your current pipeline

One major shortcoming is I manually determined the region of interest by looking as all test pictures. Luckly the test video is very simple, all the lanes we need to detect is roughly  in the same region of interest. For more general case, this methodology will not work.
Adopting more decent method is necessary for this project. For example, F-CNN has an output to detect region of interest by the algorithms. 

