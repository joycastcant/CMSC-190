# Week 7
#### (September 18, 2017 to September 22, 2017)

This week's results is focused on the limitations of the current libraries that I am using, and how I can improve them. Additionally, I used OpenMVS for creating mesh and applying texture.

As what was suggested in my latest consultation, I tried creating 3D models of simple scenes like a box of some sort. I tried doing that twice, with a variation, but the reconstruction algorithm could not find enough features to match with. 

Here is a sample from my first attempt:
[!Attempt 1](../Trials/images/rejected_box/P_20170923_154159_001.jpg)

And a sample from my second attempt:
[!Attempt 2](../Trials/images/box/P_20170923_162157_011.jpg)

In my [first attempt](../Trials/images/rejected_box), I tried to make the scene as simple as possible. Turns out, not enough features could be matched, so a reconstruction is not possible using these photos. So in my [second attempt](../Trials/images/box), I put a masking tape on the box, just to help the program see more features, but it still did not work. No reconstruction for the second set of images.

I used the box again for my [third set of images](../Trials/images/fan), but this time, I added another object:
[!Attempt 3](../Trials/images/fan/P_20170923_172930_016.jpg)

Sure, I was able to create a model, but it was not exactly desirable.
SfM:
[!SfM Fan](../Trials/models/fan/fan00.png)
PMVS:
[!PMVS Fan](../Trials/models/fan/fan_pmvs00.png)

In addition, OpenMVS could not create a denser 3d pointcloud. Although PMVS was already able to do that, I need OpenMVS to create mesh and texture, so I had to make a denser version of the model first, in MVS format. With that, I was not able to lay texture in this model.

I gave up the idea of using extremely using simple images. For my [fourth attempt](../Trials/images/shoe), I used a shoe:
[!Attempt 4](../Trials/images/shoe/P_20170923_164808_001.jpg)

I was able to create models:
SfM:
[!SfM Shoe](../Trials/models/shoe/shoe00.png)
PMVS:
[!PMVS Shoe](../Trials/models/shoe/shoe_pmvs00.png)

<INSERT MESH AND TEXTURED>

Since very simple scenes do not produce good models, I had one more attempt. For my [last attempt](../Trials/images/bear), I took photos with obvious textures and very complicated shapes:
[! Attempt 5](../Trials/images/bear/P_20170923_174438_020.jpg)

As I expected, it showed better results in all modelling techniques:
SfM:
[!SfM Bear](../Trials/models/bear/bear00.png)
PMVS:
[!PMVS Bear](../Trials/models/bear/bear_pmvs00.png)
Denser Model by OpenMVS:
[!Dense Bear](../Trials/models/bear/bear_dense00.png)
Mesh by OpenMVS:
[!Mesh Bear](../Trials/models/bear/bear_mesh00.png)
Textured Model by OpenMVS:
[!WTexture Bear](../Trials/models/bear/bear_wtexture00.png)
