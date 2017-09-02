# Week 4
#### (August 28, 2017 to September 1, 2017)

I have explored OpenCV for camera calibration, depth mapping, and 3D point cloud generation from stereo images.

### Camera Calibration
Camera Calibration is a way to correct the distortions in photos, as shown in [left03.jpg](../Trials/images/left03.jpg) (one of OpenCV's sample images).

I followed this [tutorial](http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_calib3d/py_calibration/py_calibration.html#calibration) and was able to get the following [results](../Trials/images/calibration_output/chessboard) in matching the chessboard corners. In the end, I was able to correct the distortion in [left03.jpg](../Trials/images/calibration_output/left03-new.png).

I also found [calibrate.py](https://github.com/opencv/opencv/blob/master/samples/python/calibrate.py), one of OpenCV's sample python programs, which applies the same stuff with the tutorial I followed, except that it is more detailed and complex.

### Depth Map
Stereo cameras are like human eyes, but cameras. These cameras capture (stereo) images in a way that is similar to our eyes to express a third dimension.

Stereo images are used in the next [tutorial](http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_calib3d/py_depthmap/py_depthmap.html#py-depthmap) regarding depth. The difference (or _disparity_) in the stereo images are computed to show depth -- which portions are separated from the background, and such.

Following the tutorial, I was able to generate [this](../Trials/images/disparity/parrot-disparity1.png) from these stereo [images](https://www.lhup.edu/~dsimanek/3d/stereo/parrot.jpg), with numDisparities = 16 and blockSize = 21. [This](../Trials/images/disparity/parrot-disparity2.png) is the result if numDisparities = 16 and blockSize = 11. And [this](../Trials/images/disparity/parrot-disparity3.png) is what I got when numDisparities = 32 and blockSize = 21. Looking at the results, the quality of detection depends on the values in the mentioned parameters. I am getting the hang of blockSize, but I still cannot find the pattern for numDisparities.

At the bottom of the Depth Map tutorial, I found an interesting tip. OpenCV has 3D reconstruction support using the generated disparity from stereo images..

### Creating 3D Point Cloud Using Stereo Images
There is a sample python program in OpenCV, [stereo_match.py](https://github.com/opencv/opencv/blob/master/samples/python/stereo_match.py) that does this. Running the program, it will result to two windows, (one for the original image, and another for the disparity result), and one PLY file. 

I tried their sample images first, and I saw these [results](../Trials/models/plant). Those are screenshots from MeshLab. The result is actually good. There were only two images, but OpenCV was able to generate much detail.

Of course, I tried it with the parrot images, but I keep getting [scattered points](../Trials/models/parrot-scattered.png) or [almost flat](../Trials/models/parrot-flat.png). Maybe I did not adjust the parameters enough, but as what I can see, the stereo images was not enough to express the depth that the 3D reconstruction needs. It kept putting the parrot as part of the background.

I tried the python program with another set of [images](https://www.romeartlover.it/Vasi85at.jpg). I used the first two images and tweaked the parameters once more. I was able to get better [results](../Trials/models/statue) than the parrot. As shown in the images and PLY file, the right leg of the statue was successfully captured. Although a part of the statue is clearly present, this no better than OpenCV's plant example.

If I am going to use this, I have to learn the computations they did to preset the parameters to fit the plant stereo images perfectly. In addition, I also have to know the quality of images OpenCV's 3D point cloud reconstruction works the best with.
