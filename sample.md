# Widget

{% include 'widget_start' %}
![image 1](../../../code/facetracking/versions/image1.png)
{% include 'widget_colbreak' %}<pre>
  import gab.opencv.*;
  import processing.video.*;
  import java.awt.*;

  Capture video;
  OpenCV opencv;

  void setup() {
    size(640, 480, P2D);
    video = new Capture(this, 640, 480);
    opencv = new OpenCV(this, video.width, video.height);
    opencv.loadCascade(OpenCV.CASCADE_FRONTALFACE);

    video.start();
  }

  void draw() {
    image(video, 0, 0 );

    opencv.loadImage(video);

    noFill();
    stroke(0, 255, 0);
    Rectangle[] faces = opencv.detect();
    println(faces.length);

    for (int i = 0; i < faces.length; i++) {
        rect(faces[i].x, faces[i].y, faces[i].width, faces[i].height);
    }
  }

  void captureEvent(Capture c) {
    c.read();
  }</pre>
{% include 'widget_colbreak' %}
* Comments go here.
* Another comment.
{% include 'widget_slidebreak' %}
![image 2](../../../code/facetracking/versions/image2.png)
{% include 'widget_colbreak' %}<pre>
  import gab.opencv.*;
  import processing.video.*;
  import java.awt.*;

  Capture video;
  OpenCV opencv;

  void setup() {
    size(640, 480, P2D);
    video = new Capture(this, 640, 480);
    opencv = new OpenCV(this, video.width, video.height);
    opencv.loadCascade(OpenCV.CASCADE_RIGHT_EAR);

    video.start();
  }

  void draw() {
    image(video, 0, 0 );

    opencv.loadImage(video);

    noFill();
    stroke(0, 255, 0);
    Rectangle[] ears = opencv.detect();
    println(faces.length);

    for (int i = 0; i < ears.length; i++) {
        rect(ears[i].x, ears[i].y, ears[i].width, ears[i].height);
    }
  }

  void captureEvent(Capture c) {
    c.read();
  }
</pre>{% include 'widget_colbreak' %}
* Comments go here.
* Another comment.
{% include 'widget_slidebreak' %}
![image 3](../../../code/facetracking/versions/image3.png)
{% include 'widget_colbreak' %}<pre>
  import gab.opencv.*;
  import processing.video.*;
  import java.awt.*;

  Capture video;
  OpenCV opencv;

  PImage small;
  int scaleFactor = 4;

  void setup() {
    size(640, 480, P2D);
    video = new Capture(this, 640, 480);
    opencv = new OpenCV(this, video.width/scaleFactor, video.height/scaleFactor);
    opencv.loadCascade(OpenCV.CASCADE_FRONTALFACE);

    small = createImage(opencv.width, opencv.height, ARGB);

    video.start();
  }

  void draw() {
    image(video, 0, 0 );

    small.copy(video, 0, 0, video.width, video.height, 0, 0, small.width, small.height);
    opencv.loadImage(small);

    noFill();
    scale(scaleFactor);
    stroke(0, 255, 0);
    Rectangle[] faces = opencv.detect();
    println(faces.length);

    for (int i = 0; i < faces.length; i++) {
        rect(faces[i].x, faces[i].y, faces[i].width, faces[i].height);
    }
  }

  void captureEvent(Capture c) {
    c.read();
  }
</pre>{% include 'widget_colbreak' %}
* Comments go here.
* Another comment.
{% include 'widget_end' %}