# Gesture Recognition Using Hand Pose Estimation

###Introduction
Estimate hand pose using MediaPipe (Python version).<br> Recognize hand signs and finger gestures with a MLP using the detected key points.
<br> ❗ _️**This repository is based on this [original repo](https://github.com/Lugixion/hand-gesture-recognition-mediapipe).**_ ❗<br> 

This repository contains the following contents.
* Webcam demo for gesture recognition
* Hand gesture recognition model
* Finger gesture recognition model
* Hand gesture recognition notebook for training
* Finger gesture recognition notebook for training

### Requirements
To install all the requirements run:
'$ pip install -r requirements.txt'

### webcam_demo_gesture_det.py
This is a sample demo to make real-time inference through a webcam.<br>
You can also collect training data (key point coordinates) for hand and finger gesture recognition.

### keypoint_classification.ipynb
This is a model training script for hand gesture recognition.

### point_history_classification.ipynb
This is a model training script for finger gesture recognition.

### model/keypoint_classifier
This directory stores files related to hand gesture recognition.<br>
The following files are stored.
* Training data(keypoint.csv)
* Trained model(keypoint_classifier.tflite)
* Label data(keypoint_classifier_label.csv)
* Inference module(keypoint_classifier.py)

### model/point_history_classifier
This directory stores files related to finger gesture recognition.<br>
The following files are stored.
* Training data(point_history.csv)
* Trained model(point_history_classifier.tflite)
* Label data(point_history_classifier_label.csv)
* Inference module(point_history_classifier.py)

### utils/cvfpscalc.py
This is a module for FPS measurement.

# Training
There is also a feature to add and change training data and retrain the models for hand and finger gesture recognition.

### Hand gesture recognition training
#### 1.Learning data collection
Press "k" to enter the mode to save key points（displayed as 「MODE:Logging Key Point」）<br>
If you press "0" to "9", the key points will be added to "model/keypoint_classifier/keypoint.csv" in the following structure:<br>
1st column: Pressed number (used as class ID), 2nd and subsequent columns: Key point coordinates<br>
In the initial state, three types of gestures are included: Stop (class ID: 0), Go (class ID: 1), and Point (class ID: 2).<br>
If necessary, add or delete the existing data and labels of the csv files to prepare new training data.<br>

#### 2.Model training
Open "[keypoint_classification.ipynb](keypoint_classification.ipynb)" in Jupyter Notebook and execute from top to bottom.<br>
To change the number of training data classes, change the value of "NUM_CLASSES = 3" <br>and modify the label of "model/keypoint_classifier/keypoint_classifier_label.csv".<br><br>

### Finger gesture recognition training
#### 1.Learning data collection
Press "h" to enter the mode to save the history of fingertip coordinates (displayed as "MODE:Logging Point History").<br>
If you press "0" to "9", the key points will be added to "model/point_history_classifier/point_history.csv" in the following structure:<br>
1st column: Pressed number (used as class ID), 2nd and subsequent columns: Coordinate history<br>
In the initial state, 3 types of learning data are included: None (class ID: 0), Clockwise (class ID: 1), Counterclockwise (class ID: 2).<br>
If necessary, add or delete the existing data and labels of the csv files to prepare new training data.<br>

#### 2.Model training
Open "[point_history_classification.ipynb](point_history_classification.ipynb)" in Jupyter Notebook and execute from top to bottom.<br>
To change the number of training data classes, change the value of "NUM_CLASSES = 3" and <br>modify the label of "model/point_history_classifier/point_history_classifier_label.csv". <br><br>
The user can choose between a simple MLP and a LSTM model for finger gesture recognition.<br>

# References
* [MediaPipe](https://mediapipe.dev/)
* [hand-gesture-recognition-mediapipe](https://github.com/Lugixion/hand-gesture-recognition-mediapipe)
