# real-time-face-detection

This is an OpenCV project which gets frames from your webcam and outputs as a video in real time with faces detected.

## Tutorial

Firstly we have to import the necessary libraries.

```python
import cv2, sys
```

And then denote the path to the library which is located in our folder.

```python
cascPath = "haarcascade_frontalface_default.xml"
faceCascade = cv2.CascadeClassifier(cascPath)
```

Capturing frames from webcam and assigning it to a variable for processing is done by `cv2.VideoCapture()` function. (parameter 0 for default webcam and 1,2... for USB devices)

```python
cap = VideoCapture(0)
```

Now we have to use the `detectMultiScale` [function](https://docs.opencv.org/2.4/modules/objdetect/doc/cascade_classification.html#cascadeclassifier-detectmultiscale) to detect face(s).
Let's take a look of this function's parameters:
* **image:** Matrix of the type CV_8U containing an image where objects are detected. Our type is `gray`.
* **scaleFactor:** Parameter specifying how much the image size is reduced at each image scale. In this case, we use `1.2`.
* **minNeighbors:** Parameter specifying how many neighbors each candidate rectangle should have to retain it. We will be using `5` neighbors.
* **minSize:** Minimum possible object size. Objects smaller than that are ignored. In this projects, we will be having size of `(30,30)`.

And now the functions looks like:

```python
faces = faceCascade.detectMultiScale(
    gray,
    scaleFactor=1.2,
    minNeighbors=5,
    minSize=(30, 30),
    flags=cv2.cv.CV_HAAR_SCALE_IMAGE
)
```



*to be continued...*
