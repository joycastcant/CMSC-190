# Week 10
#### (October 9, 2017 to October 13, 2017)

Finally, I was able to install OpenMVS in the other computer. The problem was the version of OpenCV that I initially installed. With that I was able to pursue other models.

I tried modeling the horse sculpture first using images, and second using a video. I also started with the paper, although I am not sure with the format.

#### Continuation of other models
Last time, I tried to model several objects to see the limitations. Here are the continuation of some of them:

##### Transparent to very shiny surface
![Shiny photo](../Trials/images/shiny/P_20170930_122056_001.jpg)
Mesh:
![Shiny Mesh](../Trials/models/shiny/shiny_dense_mesh00)
As I have suspected, this kind of surface are not modeled properly. In this sample, the parts with such surface is presented as hollow.

##### Pattern
I was able to reach the mesh for this, but I was really curious with the textured version.
![Pattern photo](../Trials/images/pattern/P_20170930_123638_001.jpg)
With Texture:
![Pattern WTexture](../Trials/models/pattern/pattern_wtexture01)
When the surface has obvious texture, the model is better.

#### Horse Sculpture
I'll only show the final models on this one.
Original:
![Horse](../Trials/images/horsep/P_20171014_122852_002.jpg)
Model:
![Horse Model](../Trials/models/horsep/horsep_dense_wtexture00.jpg)

Lowered Quality:
![Horse](../Trials/images/horsep_l/P_20171014_122852_002.jpg)
Model:
![Horse Model](../Trials/models/horsep_l/horsep_l_wtexture00.jpg)

As expected, the model was created. Lowering the quality of the images to 614x346px still created a model, but notice that there were few details this time. I lowered the quality once more, but a model is not created.

Next, I tried to take a [video](../Trials/images/horsev/horse.mp4). I only saved images every five frames because saving all frames would take me forever to model, and some of them looks practically the same.
![Horse vid](../Trials/images/horsev/50.jpg)

Sadly, a model was not created. I honestly do not know why. These images are 1920x1080px, higher than the other set of pictures I used previously, yet was able to generate a model.
