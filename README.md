# ✋ Hand Gesture Recognition with MediaPipe

## 📌 Overview
This project implements a real-time hand gesture recognition system using a webcam.   
It detects hand landmarks using MediaPipe, processes the landmark data, and classifies gestures using machine learning models. 
The application runs in real-time using OpenCV and provides visual feedback with hand skeletons, gesture labels, and FPS.   

## 🛠 Technologies Used  
Python, OpenCV, MediaPipe, NumPy   

The system supports:  
📷 Real-time webcam gesture detection  
✋ Static hand gesture recognition (hand signs)  
👉 Dynamic finger gesture recognition (motion gestures)  
🧠 Machine learning classification  
📊 Dataset logging for training new gestures  
🖥 Visual debugging interface (landmarks, bounding box, gesture labels)

## 🧠 System Architecture  
Webcam Input  
      │  
      ▼  
📷 OpenCV Frame Capture  
      │  
      ▼  
✋ MediaPipe Hand Detection  
      │  
      ▼  
📍 Landmark Extraction (21 points)    
      │  
      ├── 🧠 Static Gesture Recognition  
      │      (KeyPointClassifier)  
      │  
      └── 👉 Dynamic Gesture Recognition  
             (PointHistoryClassifier)  
      │  
      ▼  
🖥 Visualization & Display  

## 📂 Project Structure   
project/  
│  
├── app.py  
│  
├── model/  
│   ├── keypoint_classifier/  
│   │   ├── keypoint.csv  
│   │   └── keypoint_classifier_label.csv  
│   │  
│   └── point_history_classifier/  
│       ├── point_history.csv  
│       └── point_history_classifier_label.csv  
│  
├── utils/  
│   └── CvFpsCalc.py  
│  
└── README.md  

## ⚙️ Requirements
Install the required dependencies:  
pip install opencv-python mediapipe numpy  
  
Optional:  
pip install argparse    

## 🚀 Running the Application  
Run the program: 

python app.py  
Optional arguments:  
--device                (camera index (default=0))  
--width                 (capture width (default=960))    
--height                (capture height (default=540))    
--min_detection_confidence  
--min_tracking_confidence  

Example: 
python app.py --device 0 --width 1280 --height 720  

## 🎮 Keyboard Controls  
Key	Action   
ESC	❌ Exit program  
n	🔄 Normal mode  
k	📍 Log keypoint dataset  
h	👉 Log point history dataset  
0–9	🔢 Label number  
🗂 Dataset Logging  

## The system allows you to collect training data for new gestures  
📍 Keypoint Dataset  
Press: k + number (0-9)  
Saved to: model/keypoint_classifier/keypoint.csv  

👉 Point History Dataset  
Press: h + number (0-9)  
Saved to: model/point_history_classifier/point_history.csv  

🎨 Visualization  
The application overlays useful debugging information:  
✋ Hand skeleton  
📍 Finger joints  
⬛ Bounding box  
🏷 Gesture labels  
👉 Motion trail  
📊 FPS counter  

Example output:  
Right: Open  
Finger Gesture: Circle  
FPS: 30  

## 🧩 Key Functions Explained  
📍 calc_landmark_list()  
Extracts pixel coordinates of the detected hand landmarks.  

🧠 pre_process_landmark()  
Normalizes landmark coordinates so they can be used as ML features.  

👉 pre_process_point_history()  
Processes fingertip movement history for dynamic gesture recognition.  

🎨 draw_landmarks()  
Draws the hand skeleton and finger joints on the frame.  

🗂 logging_csv()  
Stores gesture data for training custom classifiers.  
