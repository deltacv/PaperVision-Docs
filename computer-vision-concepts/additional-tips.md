# Additional Tips

## Blurring

Blurring, while seemingly counter-intuitive for detection, is a vital step used to increase the reliability and robustness of your computer vision pipeline. It is almost always applied before your Color Threshold node.

### Why Blur?

The primary purpose of blurring is noise reduction and smoothing edges.

* Reduce Noise: A real-world camera feed often contains high-frequency noise, which shows up as tiny, single-pixel errors or speckles in your image. To the computer, these speckles can look exactly like small objects, leading to hundreds of false Contours after thresholding. Blurring averages out the color of these tiny noisy pixels with their neighbors, effectively making them disappear.
* Smooth Edges: Blurring helps to smooth out harsh, jagged edges caused by camera limitations or compression artifacts. This makes the boundaries of your actual target objects cleaner and more continuous, resulting in better, more accurate Contours when you run the detection phase.

### Using the Blur Node

You will use the Blur Node (found in the Image Processing category) to apply this filter.

1. Placement: Connect the output of your Pipeline Input node directly to the Blur node's Input.
2. Algorithm: The most common and effective algorithm is Gaussian Blur, which uses a weighted average that prioritizes pixels closer to the center, creating a very natural blur effect.
3. Value: This integer controls the strength of the blur.
   * Start with a low value, typically 1 or 3.
   * Increase the value slowly. A value that is too high will begin to merge your target object's color with the background, making detection impossible.

A small amount of blur is usually enough to significantly clean up the image without destroying the features you want to detect.
