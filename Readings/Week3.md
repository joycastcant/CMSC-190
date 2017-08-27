# Week 3
#### (August 21, 2017 to August 25, 2017)

This week's activities were focused on my trials in 3D modelling and image processing. I did less paper reading, and looked at bunch of tutorials.

### 3D Reconstruction Using Handheld Camera
Unlike the other studies that used special cameras (ie. [stereo cameras](http://www.vmresource.com/camera/cameras-general.htm)), the study entitled, [3D Reconstruction from Image Sequence Taken with a Handheld Camera](Documents/3d_Reconstruction_from_Image_Seq_Taken_with_a_Handheld_Camera.pdf) used the type of camera that is not hard to acquire.

These are the main algorithms used in the study:
1. SIFT Algorithm
  * used for recognizing features in the images
2. Euclidean Distance
  * points between images are measured for similarity. The smaller the computed value is, the more similar the points are
3. [Eight-point Algorithm](http://www.cs.unc.edu/~marc/tutorial/node54.html)
  * used to refine the recognized matches by estimating the fundamental matrix using eight or more points
 
Looking at the final parts, it seems that their research did not show grand results as compared with the other papers I have read where special cameras are used. But to be fair, they only used point matching here. There were no silhouettes, color information, patching, or snakes. The whole 3D reconstruction was riding on the capability of the algorithms that they used. 

### Trials

#### Cube
There were not much references in PLY files, so I had to break down the code myself. This [link](http://paulbourke.net/dataformats/ply/) helped me alot in understanding PLY files. The explanation there was alright, except for the _facelist_ part:
```ply
4 0 1 2 3 
4 7 6 5 4
4 0 4 5 1
4 1 5 6 2
4 2 6 7 3
4 3 7 4 0
```

I'll try to explain this portion. The way I understood it, the first number in every line is the number of corners (or maybe sides) of the shape. Since they are all _four_, it would mean that there are six quadrilaterals. The other next numbers represents the points of each corner assigned to them as shown in this [image](https://goo.gl/photos/mxBWb3AQQGSkLuH88).

Here's the [STL version](../Trials/models/cube.stl) of the cube from the website (I converted it so it can be viewed from Github).

#### Feature Matching
Finally, I have found a [tutorial](http://docs.opencv.org/trunk/dc/dc3/tutorial_py_matcher.html) for this. Well, the tutorial already gives me the code to do it, but I still have to understand it so I can use it for other purposes.

Although the code is already there, making it work in my device was a challenge. The brute-force algorithm worked well in my device as shown [here](../Trials/images/books.png). I'm amazed as to how it happened using OpenCV and Python. Even with that, I do not want to settle for brute-force. The tutorial included a SIFT algorithm one, which should work better. After a series of uninstalling and reinstalling several versions of OpenCV, I still could not make SIFT work.

OpenCV already has a function for brute-force matching, so it was really convenient.

---
UPDATE: As of August 27, 2017, I finally made SIFT work. The result is [here](../Trials/images/books_SIFT.png).
