# Week 5
#### (September 4, 2017 to September 8, 2017)

For this week, I tried to create 3D Model from series of images, instead of [stereo images](https://github.com/joycastcant/CMSC-190/blob/master/Readings/Week4.md) only.

I used the [OpenMVG](https://github.com/openMVG/openMVG) library. Here is an [example](https://www.youtube.com/watch?v=q93wH-F58Rs) of what it can do. There is also an available [GUI](https://www.youtube.com/watch?v=Q2_cVN902-M) to use it, but I chose to study what it does using the codes. I used the Structure from Motion technique to estimate the 3D features using 2D images. It is readily available in OpenMVG. In fact, a [sample code](https://github.com/openMVG/openMVG/blob/master/src/software/SfM/tutorial_demo.py.in) using SfM is there to demonstrate the power of the library.

Here are the [images](../Trials/images/openMVG/jake) that I used. There are 22 images in total.

### Process
I was not able to use the file smoothly at first because the library does not have my phone's camera specifications. I had to add it: Model: ASUS_ZOOLD, Sensor size: 4.7. Once I am done with that, the program started processing the images.

1. [Intrinsics Analysis](http://openmvg.readthedocs.io/en/latest/software/SfM/SfMInit_ImageListing/)
* the images are collected as _views_ containing their name, size, and internal camera calibration information
* each view has corresponding pose and group (_group_ means that other views has similar parameters)

2. [Compute Features](http://openmvg.readthedocs.io/en/latest/software/SfM/ComputeFeatures/)
* uses the data from each view collected in the first step
* uses SIFT method by deafult to get features

3. [Compute Matches](http://openmvg.readthedocs.io/en/latest/software/SfM/ComputeMatches/)
* the same data from step 1 is still needed
* putative matches: pairs of images that matched by SIFT and the distance ratio test
* geometric matches: pairs of images that passed the robust model estimation test
(Last two descriptions are from [here](https://github.com/openMVG/openMVG/issues/315))

4. 3D Reconstruction
* [Sequential/ Incremental Reconstruction](http://openmvg.readthedocs.io/en/latest/software/SfM/IncrementalSfM/)
  * each edge is processed sequantially, much like its name
* [Global Reconstruction](http://openmvg.readthedocs.io/en/latest/software/SfM/GlobalSfM/)
  * removes false pairs
  * refinement done by two-step bundle adjustment: structure and translations, and structure and camera parameters

5. [Colorize Structure](http://openmvg.readthedocs.io/en/latest/software/SfM/ComputeSfM_DataColor/)
* from the list of colorless tracks, the track which can be seen from the view is colored
* this is done until all tracks are colored

6. [Structure from Known Poses](http://openmvg.readthedocs.io/en/latest/software/SfM/ComputeStructureFromKnownPoses/)
* robust triangulation
* image triplets that has similar content are collected
* for each triplet: if they are triangulable, they are recorded as tracks then rebustly triangulated

Written above are the simplified versions of how to reconstruct 3D models using OpenMVG. It has similar steps with the one in OpenCV, so it was a little easier for me to understand them now.

### Results
Snapshots of the model from sequential reconstruction are [here](../Trials/models/jake/sequential), and the PLY file is [here](../Trials/models/jake/sequential/jake_seq.ply). In global reconstruction, the images are [here](../Trials/models/jake/global), and the PLY file is [here](../Trials/models/jake/global/jake_global.ply).

The green cubes floating above the model are the computed camera poses (from step 1). I am lacking in number of pictures so the model still has holes, but the toy can be recognized. The color of the toy and the eyes can be seen. The bump it created on the surface from being placed there is also applied. This is very different from the disparity-based reconstruction from Week 4, where some parts of the images are recognized as backgrounds, or the model is only composed of scattered, unrecognizable points.
