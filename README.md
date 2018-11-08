# Face Recognition
Recognize faces from Python or from the command line with the use of a very popular image and video processing library.

# Features
Find all the faces that appear in the real-time video stream.

# Installation
Requirements:
* Python 3.3+ or Python 2.7

Installation on Windows:
```pip install opencv-python```

Installation in Anaconda:
```conda install -c conda-forge opencv```

# Python Code
``` 
import cv2

cap = cv2.VideoCapture(0)

# Haar cascade creation
faceCascade = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")

while(True):
	# Capture frame-by-frame
	ret, frame = cap.read()

	gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

	# Detect faces in the image
	faces = faceCascade.detectMultiScale(
		gray,
		scaleFactor=1.1,
		minNeighbors=5,
		minSize=(30, 30)
		#flags = cv2.CV_HAAR_SCALE_IMAGE
	)

	print("Found {0} faces!".format(len(faces)))

	# Draw a rectangle around the faces
	for (x, y, w, h) in faces:
		cv2.rectangle(frame, (x, y), (x+w, y+h), (0, 255, 0), 2)


	# Display the resulting frame
	cv2.imshow('frame', frame)
	if cv2.waitKey(1) & 0xFF == ord('q'):
		break

# When everything done, release the capture
cap.release()
cv2.destroyAllWindows()
```

# Output

# Reason why I chose this topic
Upon the completion of my Machine learning and Deep Learning course at Coursera.com I learned the various applications of the same. Facial Recognition was one of the applications which attracted me to work on
and then I applied my knowledge to create facial recognition code with the help of OpenCV library which detects multiple faces in real-time video stream using my webcam or any external camera.
This code can also be modified to be used on RaspberryPi.
