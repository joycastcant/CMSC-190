# Week 6
#### (September 11, 2017 to September 15, 2017)

Exploring OpenMVG, I have found out that I should focus on using this library now, instead of OpenCV. While OpenCV provides functions that I can use in 3D reconstruction, OpenMVG is more devoted to multiple views, so it is easier to use. OpenMVG can be used together with OpenCV, so I can still use the latter when I need it.

For this week, I was able to produce better 3D models by using PMVS (Patch-based Multi-view Stereo Software) and CMVS (Clustering Views for Multi-view Stereo)

First, I added few lines at the end of the demo code last week:
```
pRecons = subprocess.Popen( [os.path.join(OPENMVG_SFM_BIN, "openMVG_main_openMVG2PMVS"),  "-i", reconstruction_dir+"/sfm_data.bin", "-o", os.path.join(reconstruction_dir)] )
pRecons.wait()
```

  _openMVG_main_openMVG2PMVS_ is a bin file in the built version of the library (source code availble [here](https://github.com/openMVG/openMVG/blob/master/src/software/SfM/main_openMVG2PMVS.cpp)). This is where poses are re-indexed (from valid cameras), and images are undistorted. This so that camera parameters will be properly computed for our bundler. All these are acquired from the raw images and the SfM data created in the previous steps.
  
I also followed these [steps](http://openmvg.readthedocs.io/en/latest/software/MVS/PMVS/) except that I changed the last line to ```pmvs2 Dataset/outReconstruction/PMVS/ option-xxxx```. The given last line does not work because the sh file tries to access non-existent directory.

I used [53 images](..Trial/images/jake_burst) in producing the following results:

#### Global Reconstruction
SfM:
![SfM](../Trial/models/jake_on_laptop/global/jake_laptop00.png)

PMVS:
![SfM](../Trial/models/jake_on_laptop/global/pmvs/jake_laptop_pmvs00.png)
