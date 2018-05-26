# Improved Seam Carving Using Forward Energy

>Seam-carving is a content-aware image resizing technique where the image is reduced in size by one pixel of height (or width) at a time. A vertical seam in an image is a path of pixels connected from the top to the bottom with one pixel in each row. Unlike standard content-agnostic resizing techniques (such as cropping and scaling), seam carving preserves the most interesting features (aspect ratio, set of objects present, etc.) of the image.

This was the description of seam carving in an [assignment](https://www.cs.princeton.edu/courses/archive/spring16/cos226/assignments/seamCarving.html)
for my Algorithms & Data Structures class.

Below top is a 512-by-342 pixel image; below left and right are the results after removing 200 vertical seams using two different methods. The first method is the one taught in many CS curriculums, including CS 61B at UC Berkeley and mine. The second method should have been taught as well, since it's a better algorithm that preserves the water gradient and bench supports.

In this notebook, I will be implementing both methods using numpy and scikit-image.

<img src="doub_bench3_comp.jpg" alt="seam" width=500>

For more details, read the original [seam carving paper](http://www.faculty.idc.ac.il/arik/SCWeb/imret/index.html) 
and the [Improved Seam Carving](http://www.faculty.idc.ac.il/arik/SCWeb/vidret/index.html) paper.

Both papers introduce different ways to "calculate the energy of a pixel, which is a measure of its importance—the higher the energy, the less likely that the pixel will be included as part of a seam."

The first paper calculated the energy of a pixel using an edge detection algorithm called dual gradient (backwards energy).

The second paper calculated the energy of a pixel depending on how much energy would be added to the image after its removal, called forward energy.

The two resulting energy maps of the bench image using the two methods look like this, where higher energy pixels are brighter:

<img src="eimg.jpg" alt="eimg" width=700>

As you can see, seams will not want to pass through the bench using backwards energy, which causes severe artifacts. The forward energy algorithm doesn't, and the results are similar to what happens in Adobe Photoshop.

I believe my implementation of forward energy is more optimal than any other implementation I've seen on Google or GitHub, though I note more potential optimizations in the notebook.

I hope to add it to scikit-image's seam_carve function.

For implementation details (tested on a nondescript Windows laptop), please view the notebook here for the best formatting and not directly on GitHub:

https://nbviewer.jupyter.org/github/axu2/improved-seam-carving/blob/master/Improved%20Seam%20Carving.ipynb

## Examples

![examples](examples.png)
