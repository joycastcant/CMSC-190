# Week 1
#### (August 7, 2017 to August 11, 2017)

### Predicting products of chemical reactions
Back in high school, I used to have a problem in telling what chemical appears when I combine chemical A with a bunch of other chemicals. Sure, there are patterns, but they are incredibly hard to remember (at least for me). Imagine dragging chemicals off their pane to a panel where the prediction will happen. If someone just wanted to know what happens when he mix heroin with cocaine, he does not have to look all over the place for them, and does not have to spend as much money.

I consulted Google if a project like this already exists, or if a similar one does. It took me to a 2017 [article](http://news.mit.edu/2017/computer-system-predicts-products-chemical-reactions-0627) in MIT News. According to it, an end-product chemical does not have a single combination of chemicals. There are many paths to get there. Essentially, they want to be able to know which chemicals they should combine to get the desired product. It is the reverse of what is in my mind.

After sometime, I found a study entitled, [A Machine Learning Approach to Predict Chemical Reactions](Documents/A_Machine_Learning_Approach_to_Predict_Chemical_Re.pdf) which seems to match my idea. Unlike other chemical reaction predicting programs which uses plain database, they used machine learning to do it. Specifically, they used _artificial neural networks with a one hidden layer, and one node for output_. As I read the paper, I learned that there are so much to consider in predicting chemical reactions. It does not end with the chemicals themselves. I also have to know the conditions of the environment, such as temperature and humidity. This study focused in organic chemistry (the area of chemistry I am most familiar with), but there are other areas that were not included. I learned that using machine learning is already complicated itself, and the topic adds to the complication. I am no genius in machine learning and chemistry, so I will need help to understand both more.

### Calculating the speed of an object using video
This one already exists in the current age. Video analysis is the usual answer for it. The simplest explanation I got was from [topendsports.com](http://www.topendsports.com/biomechanics/video-analysis-speed.htm). The distance the object travelled and the frame rate of the video both matter. The idea that a video is a series of images recorded must be kept in mind for there will always be delays in the video depending on the frame rate, as briefly explained in the mentioned website.

There was also a thesis dated in the year 2000 regarding video object detection and segmentation: [Algorithms for Video Object Detection and Segmentation with Application to Content-Based Multimedia Systems](http://www.ee.columbia.edu/ln/mmsp/papers/thesis-hluo.pdf).

There were three approaches mentioned for video object segmentation:
1. Foreground and background segmentation
  * With the assumption that everything in the background is static,
  the focus will be in the foreground.
2. Motion field segmentaion
  * Motion fields dictates where the object is.
3. Multiple image feature based segmentation algorithms
  * Typically uses combination of color and motion segmentation.

Face detection algorithms classification were also mentioned in video object detection:
* Color-based approach
* Texture-based approach

There were also a lot of processes done. Some of them were blob-based tracking and shape recognition. I saw lots of algorithms and figures that I admittedly do not fully understand yet.

Image processing can also be a way, as presented by the paper, [Speed Detection Camera System using Image Processing Techniques on Video Streams](http://www.ijcee.org/papers/418-E1077.pdf). It records the frame number the object appeared in the video, and the frame number it exited. The number of frames it took to leave the scene will be computed. Using that and the knowledge of the video's frame rate, the time it took or the object to pass can now be calculated. The formula for speed can then be used.

### 3D reconstruction of objects from multiple images
I got this idea from an article in ScienceDaily. [FlowRep](https://www.sciencedaily.com/releases/2017/08/170801094351.htm) constructs 3D skeleton sketches and reconstructions from an input model. For better appreciation, please watch this [video](https://youtu.be/en7ICJRGzH0).

Turns out, there were already numerous attempts on this, as I found out from this pdf [file](https://people.csail.mit.edu/sparis/talks/Paris_06_3D_Reconstruction.pdf).
1. Reconstruction from Consistency Only
2. Minimal Surfaces with Level Sets
3. Snakes
4. Minimal Surfaces with Graph Cut
5. Exploiting Silhouettes
6. Multi-scale Approach
7. Patchwork Approach

On the base level, a feature is matched in consecutive images to _"continue the object"_. Although there are numerous mentioned approaches, all of these only tackle a controlled setup. These, by themselves, does not apply to outdoor and/or moving objects. I have not read specific sources for each of the approaches yet, so I do not have a big idea out of them at the moment. For now, I am interested in combining approaches 1, 4, 5 and 7, if possible.