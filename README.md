## Project Report: Vehicle Detection and Tracking using YOLO and dlib

**1. Introduction**

This project aims to develop a system for real-time vehicle detection and tracking in a video stream. The system utilizes the YOLO (You Only Look Once) object detection algorithm for initial detection and dlib's correlation tracking for subsequent tracking of detected objects. The project also incorporates a vehicle counting feature, categorizing vehicles into cars, trucks, vans, bikes, and jeeps.

**2. Objectives**

* Implement real-time vehicle detection using the YOLOv3 model.
* Implement real-time vehicle tracking using dlib's correlation tracking.
* Categorize and count different types of vehicles (cars, trucks, vans, bikes, jeeps).
* Display the detected objects with bounding boxes, labels, and vehicle counts.

**3. Methodology**

**3.1. Object Detection (YOLOv3)**

* The YOLOv3 model, pre-trained on the COCO dataset, is used for object detection.
* The model is loaded using OpenCV's `dnn.readNet` function, with the corresponding weights (`yolov3.weights`) and configuration (`yolov3.cfg`) files.
* The `detect_objects` function processes each frame by:
    * Creating a blob from the frame, which is the input format for the YOLO model.
    * Feeding the blob to the YOLO network.
    * Extracting the detected objects, their bounding boxes, and confidence scores.
    * Filtering detections based on a confidence threshold (0.5).
    * Storing the detected objects with their bounding box coordinates and class labels.

**3.2. Object Tracking (dlib)**

* dlib's correlation tracking is used to track the detected objects across frames.
* The `object_tracking` function initializes a list of dlib trackers and object IDs.
* For each detected object:
    * It checks if an existing tracker overlaps with the detected object's bounding box.
    * If a tracker is found, it updates the tracker with the new frame.
    * If no tracker is found, a new dlib tracker is created and initialized with the object's bounding box.
* The trackers are used to track the objects' positions in subsequent frames.

**3.3. Vehicle Counting and Categorization**

* The project categorizes vehicles into cars, trucks, vans, bikes, and jeeps based on the class labels provided by the YOLO model.
* Counters are maintained for each vehicle type.
* When a vehicle is detected, the corresponding counter is incremented based on its label.

**3.4. Display**

* The detected objects are displayed with bounding boxes and class labels.
* The vehicle counts are displayed on the video frame.
* `cv2_imshow` from google colab patches is used for displaying video in google colab.

**4. Implementation**

* The project is implemented in Python using the OpenCV, dlib, NumPy, and google colab patches libraries.
* The YOLOv3 model and COCO class names are loaded from local files.
* The `detect_objects` and `object_tracking` functions are implemented as described in the methodology.
* The code is designed to run in google colab, and use the google colab patches for video display.

**5. Results**

* The system successfully detects and tracks vehicles in the video stream.
* The vehicle counts are accurately displayed.
* The system is able to differentiate between car, truck, van, bike and jeep objects.

**6. Discussion**

* The use of YOLO for object detection provides accurate and efficient initial detection.
* dlib's correlation tracking effectively tracks the objects across frames, even with moderate motion and occlusion.
* The vehicle counting feature provides valuable information about the traffic composition.
* The code can be further improved by adding features like vehicle speed estimation and traffic flow analysis.
* The accuracy of the vehicle counting can be improved by refining the label matching logic.
* The performance can be improved by using a more optimized version of YOLO, such as YOLOv4 or YOLOv5.

**7. Conclusion**

This project demonstrates the feasibility of real-time vehicle detection and tracking using YOLO and dlib. The system effectively detects and tracks vehicles, categorizes them, and displays the results. The project provides a foundation for further development of advanced traffic monitoring and analysis systems.

**8. Future Work**

* Implement vehicle speed estimation.
* Perform traffic flow analysis.
* Integrate the system with a database for data storage and retrieval.
* Deploy the system on an edge device for real-time processing.
* Improve the accuracy of the detection by training the YOLO model on a custom dataset of vehicles.
* Implement a method to handle occlusions more effectively.
* Implement a method to handle vehicles that change direction rapidly.
