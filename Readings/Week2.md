# Week 2
#### (August 14, 2017 to August 18, 2017)

For this week, the focus is on the 3D reconstruction of objects from multiple images. Listed below are the approaches that I think will be of help in this topic.

### Reconstruction from Consistency
Photo consistency is one of the main things to be considered in reconstructing 3D objects from images. In fact, it plays a role in all of the approaches to be mentioned here.

Here is a study focusing on photo consistency with a twist: [3D Reconstruction Using Photo Consistency from Uncalibrated Multiple Views](Documents/3D_RECONSTRUCTION_USING_PHOTO_CONSISTENCY_FROM_UNCALIBRATED_MULTIPLE_VIEWS.pdf). As the title suggests, it uses photo consistency and planar homography (follow this [link](http://www.learnopencv.com/homography-examples-using-opencv-python-c/) for a simple explanation of what homography is) to generate 3D objects. The edge of this approach is that it does not require camera pose and calibration. It also uses smaller number of views compared with other approaches requiring calibration and pose (the paper included two of its experiments which used 48 photos and 33 photos). Compared with the silhouette-based reconstruction approach, it can estimate concave and convex parts of the object better.

Below are the simplified concepts in the paper:
* Mapping the relation of the 3D object with the images
* Utilizing color information

### Minimal Surfaces with Graph Cut
A paper entitled [Multi-view Stereo via Volumetric Graph-cuts](ftp://svr-ftp.eng.cam.ac.uk/pub/reports/vogiatzis_cvpr2005.pdf) used graph cuts and silhouttes in creating 3D objects.

They combined the methods below and utilized the advantages of each one:
* Graph-cuts
* Loppy Belief Propagation
* Space Carving
* Level Set Stereo

A human face synthetic scene is presented in the paper. They used eight images, which is way smaller than the number used in the study focusing on photo consistency only.

Comparisons between other methods were shown, and their method, 2-view Belief Propagation showed best results, considering the number of images they used. Concavities and details were successfully detected. Their method guarantees convergence, and presents higher accuracy.

### Exploting Silhouettes
The use of silhouettes has been mentioned in the previous studies, as something "not good enough". Even with that, a study came from it and improved the method: [Silhouette-based 3D Model Reconstruction from Multiple Images](https://www.cv.tu-berlin.de/fileadmin/fg140/Silhouette-based_3D.pdf).

The study added photo consistency, triangulation, and texture mapping to the system, instead of using silhouette extraction alone.

The following are the simplified steps used in this study:
1. Estimation of bounding box of the object to be reconstructed.
2. Projection of cubes in 3D space to the images (only those that are in the silhouette region).
3. Tuning using photo consistency
4. Triangulation and Texture Mapping

The results in this study showed promising results, successfully removing excess [voxels](http://whatis.techtarget.com/definition/voxel), which is a common problem in silhouette-based approach.

### Patchwork
As the name suggests, it is an approach which creates 3D objects part by part. The study entitled [Accurate and Scalable Surface Representation and Reconstruction from Images](Documents/MIT-CSAIL-TR-2005-076.pdf) can help us understand it better.

The study has two categories depending on how fine the details are. Patch consistency is used in carving on the coarse level, while minimal cuts build the patches that are stitched on the fine level. 

The approach was able to get accurate results, and capture concavities. In addition, it was able to produce seamless 3D object even if there are hidden regions in the available images.

Essentially, small pieces are acquired and stitched together to reconstruct a 3D object.

---

I looked for tutorials in creating 3D objects, but all I could see are those that are created using editing softwares. I have tried to create a [3D model](https://goo.gl/photos/5Lahr8bdKtsYJi519) using Photoshop. For next week, I will try to create a 3D object by programming.
