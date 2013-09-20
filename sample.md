#### Luma: A More Accurate Measure of Brightness

[Luma](http://en.wikipedia.org/wiki/Luma_%28video%29) is a representation of the brightness of a pixel that matches human perception more accurately than its gray value, which is a simple average of the reg, green, and blue components. Luma can be calculated as an unequal combination of the red, green and blue components of the pixel according to the following formula: 0.2126\*R + 0.7152\*G + 0.0722\*B. To use Luma for brightness tracking with our OpenCV image, you could iterate through the image and calculate the Luma value for each pixel, which would be slow. Or, you could use OpenCV's <code>[Imgproc.cvtColor()](http://docs.opencv.org/java/org/opencv/imgproc/Imgproc.html#cvtColor)</code> function in concert with <code>opencv.getBufferColor()</code> to convert the image to the [LAB color space](https://en.wikipedia.org/wiki/Lab_color_space), which includes Luma as one of its three channels.

This image demonstrates the comparison. The difference can be subtle. Click through to the larger size to make sure you see it. Look carefully at the right side of the image around the flashlight.

<a href="http://www.flickr.com/photos/unavoidablegrain/9228785034/" title="Gray vs Luma by atduskgreg, on Flickr"><img src="http://farm3.staticflickr.com/2829/9228785034_39c665d9e9.jpg" width="500" height="358" alt="Gray vs Luma"></a>

### Quiz

Q: What qualities of our input image could cause problems with brightness tracking: A) The presence of many glowing objects. B) Moving shadows cast by passersby. C) The auto-exposure on our camera triggering. D) All of the above.

{% include "answer" with "D, all of the above." %}

Q: Which are easier to track with this version of color tracking: bright red or dark red objects?