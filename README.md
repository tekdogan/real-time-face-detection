# real-time-face-detection

This is an OpenCV project which gets frames from your webcam and outputs as a video in real time with faces detected. We will be using *Haar Feature-based Cascade Classifiers* for face detection. You can learn more about it by clicking [here](https://docs.opencv.org/3.4/d7/d8b/tutorial_py_face_detection.html).

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

Capturing frames from webcam and assigning it to a variable for processing is done by `cv2.VideoCapture()` [function](https://docs.opencv.org/2.4/modules/highgui/doc/reading_and_writing_images_and_video.html?highlight=get#VideoCapture). (parameter 0 for default webcam and 1,2... for USB devices)

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


For every face detected by `detectMultiScale` function, we draw a red rectangle around it.

```python
    for (x, y, w, h) in faces:
        cv2.rectangle(frame, (x, y), (x+w, y+h), (0, 0, 255), 2)
```

And yield the output as a frame.

```python
    cv2.imshow('Face Detection Program', frame)
```

Press `esc` key to close the window and shut down the program.

```python
   if cv2.waitKey(1) & 0xFF == 27:
        break

cap.release()
cv2.destroyAllWindows()
```









*to be continued...*
