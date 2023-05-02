Download Link: https://assignmentchef.com/product/solved-comp9517-assignment1-basic-image-processing-methods
<br>
This assignment is aimed at familiarisation with basic image processing methods. It also introduces you to common image processing and analysis tasks using OpenCV. After completing this assignment, you will know how to:

<ol>

 <li>Open and read image files.</li>

 <li>Display and write image files.</li>

 <li>Perform mathematical operations on images.</li>

 <li>Apply basic image filtering operations.</li>

 <li>Perform image adjustment and restoration.</li>

</ol>

<strong>Description: </strong>

Many computer vision applications use image processing techniques to suppress artifacts and enhance relevant features to prepare images for further quantitative analysis.

The goal of this assignment is to create an image processing algorithm that can open a digital image, perform a sequence of pixel manipulation operations (step-by-step as listed under <strong>Tasks</strong>), in order to remove background shading artifacts.

Below is an image (on the left) from a biological experiment in which the researchers want to measure several properties of the dark particles. But these measurements are impeded by the shading in the background. Thus, the shading needs to be removed (as on the right).

<strong>Tasks: </strong>

This assignment consists of three tasks, described below. Each task depends on the previous one, so you need to do them in the given order.




<h1>Task 1 (4 marks): Background estimation</h1>

Open the given image <strong>Particles.png</strong> which, similar to the example shown above, has a background shading pattern that needs to be removed. The first step to get rid of the shading is to make an accurate estimate of the background of the image.




Write an algorithm that performs the following two steps. First, it should create a new image, let us call it image A, with the same size (number of pixel rows and columns) as the input image, which we call I. Second, the algorithm should go through the pixels of I one by one, and for each pixel (x,y) it must find the <strong>maximum</strong> gray value in a neighbourhood around that pixel, and write that maximum gray value in the corresponding pixel location (x,y) in A. The resulting image A is called a <strong>max-filtered</strong> image of input image I.

The neighbourhood should be of size N x N pixels, where N is a free parameter of the algorithm. Experiment with different values of N and mention in your report what is the smallest value of N that causes the dark particles in I to disappear altogether in image A. Also explain why this value of N causes the particles to disappear.

The max-filtering causes the gray values in A to be higher than the actual background values in I, so a correction is needed. Extend your algorithm to create another image, which we call image B here, of the same size as I and A. Now let the algorithm go through the pixels of A one by one, and for each pixel (x,y) find the <strong>minimum</strong> gray value in an N x N neighbourhood around that pixel, and write that minimum gray value in (x,y) in B. The resulting image B is called a <strong>min-filtered</strong> image of the image A.

In your report, include image B computed from <strong>Particles.png</strong>.

<h1>Task 2 (2 marks): Background subtraction</h1>

Now that your algorithm can estimate the background B of an image I, removing the shading artifacts from I can be done simply by subtracting B pixel by pixel from I, resulting in the output image O. Extend your algorithm to perform this subtraction.

In your report, include image O computed from <strong>Particles.png</strong>.

<h1>Task 3 (4 marks): Algorithm generalisation</h1>

Open the given image <strong>Cells.png</strong> which, similar to <strong>Particles.png</strong>, has a background shading pattern that needs to be removed. There are three main difference between the two images: 1) the sizes of the images are different; 2) the sizes of the objects (cells versus particles) are different; 3) in <strong>Cells.png</strong> the objects are bright and the background is dark, whereas in <strong>Particles.png</strong> the objects are dark and the background is bright.

Make sure your algorithm can deal with input images of arbitrary size. Dealing with larger objects in images is a matter of changing the value of the neighbourhood parameter N. But as you will see, your algorithm will not be able to remove the shading from <strong>Cells.png</strong>. To make your algorithm work for that image, you need to reverse the max-filtering and min-filtering.

Extend your algorithm with another free parameter, named M. If the user sets M = 0, the algorithm should perform max-filtering (image I to A), then min-filtering (image A to B), then subtraction (O = I – B). And if the user sets M = 1, the algorithm should perform first min-filtering, then max-filtering, then subtraction.

In your report, explain why <strong>Particles.png</strong> requires M = 0, and <strong>Cells.png</strong> requires M = 1. Also mention what is a good value of N for <strong>Cells.png</strong> and why. And include images B and O computed from <strong>Cells.png</strong> in your report.