# Improved Seam Carving

After implementing the original seam carving algorithm in a class,
I read the improved seam carving paper by the same author. 

The difference between the two methods can be shown in the below photo from the paper:

<img src="doub_bench3_comp.jpg" alt="seam" width=500>

where the top is the original photo, the left is the carving I implemented in class, and the right is the improved carving.

I decided to implement these functions using numpy and scikit-image.

I believe my implementation of forward energy is more optimal than any other implementation I've seen on Google or GitHub, though I note more potential optimizations in the notebook.

Please view the notebook here for the best formatting and not directly on GitHub:

https://nbviewer.jupyter.org/github/axu2/improved-seam-carving/blob/master/Improved%20Seam%20Carving.ipynb
