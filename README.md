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

Capturing frames from webcam and assigning it to a variable for processing is done by cv2.VideoCapture() function. (parameter 0 for default webcam and 1,2... for USB devices)

```python
cap = VideoCapture(0)
```

*to be continued...*
