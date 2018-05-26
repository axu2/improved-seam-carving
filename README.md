For implementation details and the full description, please view the notebook here for the best formatting and not directly on GitHub:

https://nbviewer.jupyter.org/github/axu2/improved-seam-carving/blob/master/Improved%20Seam%20Carving.ipynb

# Improved Seam Carving Using Forward Energy

>Seam-carving is a content-aware image resizing technique where the image is reduced in size by one pixel of height (or width) at a time. A vertical seam in an image is a path of pixels connected from the top to the bottom with one pixel in each row. Unlike standard content-agnostic resizing techniques (such as cropping and scaling), seam carving preserves the most interesting features (aspect ratio, set of objects present, etc.) of the image.

This was the description of seam carving in an [assignment](https://www.cs.princeton.edu/courses/archive/spring16/cos226/assignments/seamCarving.html)
for my Algorithms & Data Structures class.

Below top is the original 512-by-342 pixel image; below left and right are the results after removing 200 vertical seams using two different methods.

<img src="doub_bench3_comp.jpg" alt="seam" width=500>

The two methods are described in the original [seam carving paper](http://www.faculty.idc.ac.il/arik/SCWeb/imret/index.html) 
and the [Improved Seam Carving](http://www.faculty.idc.ac.il/arik/SCWeb/vidret/index.html) paper.

Both papers introduce different ways to "calculate the energy of a pixel, which is a measure of its importance—the higher the energy, the less likely that the pixel will be included as part of a seam."

The first paper (which I implemented in class) calculated the energy of a pixel using an edge detection algorithm called backwards energy.

The second paper calculated the energy of a pixel depending on how much energy would be added to the image after its removal, called forward energy.

The two resulting energy maps of the bench image using the two methods look like this, where higher energy pixels are brighter:

<img src="eimg.jpg" alt="eimg" width=700>

As you can see, seams will not want to pass through the bench using backwards energy, which causes the water gradient and the bench support to suffer severe artifacts. The forward energy algorithm doesn't, and the results are similar to what happens in Adobe Photoshop.

So I decided to implement both forms of energy of energy using numpy and scikit-image, testing on a nondescript Windows laptop using Anaconda.

I believe my implementation of forward energy is more optimal than any other implementation I've seen on Google or GitHub, though I note more potential optimizations in the notebook.

I hope to add it to scikit-image's seam_carve function.

## Examples

![examples](examples.png)
