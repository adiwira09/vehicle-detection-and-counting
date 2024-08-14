# Vehicle Detection and Counting using YOLOv8, Supervision and ByteTrack
This project implements a vehicle detection and counting system using the YOLOv8 model and ByteTrack tracker. The system processes video footage, identifies vehicles (specifically cars and buses), tracks their movements, and counts them as they pass a predefined line.

## Project Overview
- Model: The YOLOv8 model (yolov8x.pt) is used for object detection, focusing on identifying specific vehicle classes (cars and buses).
- Tracker: ByteTrack is utilized to track detected vehicles across video frames.
- Video Input: The system processes a video file (toll_gate.mp4) where vehicles move through a toll gate.
- Output: The system generates an annotated video (toll_gate-result.mp4) showing detected vehicles with bounding boxes, labels, and a count of vehicles that cross a designated line.

## Execution Platforms
This notebook has been tested and executed on the following platforms with GPU acceleration:
- Google Colab
- Kaggle
** Using GPU accelerators significantly speeds up the detection and tracking processes.

## File Definitions
- `requirements.txt`: Lists the required libraries to run the project.
- `assets/toll_gate.mp4`: Input video file for vehicle detection.
- `assets/toll_gate-result.mp4`: Output video file with detection results and vehicle counts.
- `notebook.ipynb`: Jupyter notebook containing the code for the project.
- `yolov8x.pt`: YOLO Pre-Trained model.

## Features
- Vehicle Detection: YOLOv8 is used to detect objects in the video, with a focus on detecting cars (class 2) and buses (class 5).
- Tracking: ByteTrack is implemented to track detected vehicles across multiple frames, ensuring accurate counting.
- Line-based Counting: A line is defined within the video frame, and vehicles crossing this line are counted. The position of this line can be customized.
- Annotations: The system adds bounding boxes, tracking traces, and labels to the video to visually represent detected vehicles. It also annotates the line used for counting and displays the vehicle count in the video.

### Input Video (Before Detection)
https://github.com/user-attachments/assets/62067b98-3ce8-4458-b030-2fe22b92f99b

### Output Video (After Detection and Counting)
https://github.com/user-attachments/assets/6fb2f106-1313-4a4b-9e91-b5abfb9dab1a

## Key Sections in the Code
1. Install and Import Libraries: The notebook installs the necessary libraries (`ultralytics`, `supervision`, `numpy`, `tqdm`) and imports them for use in the project.
2. Load the YOLOv8 Model: The YOLOv8 model is loaded and optimized for faster inference by fusing the layers.
3. Load and Process Video: The input video (assets/toll_gate.mp4) is loaded, and a generator is set up to read the video frame by frame.
4. Setup Detection and Tracking:
- The system sets up the ByteTrack tracker to handle object tracking.
- A line is defined in the video frame that will be used to count vehicles as they cross it.

5. Annotate and Save Results:
- For each video frame, the system performs detection and tracking.
- Detected vehicles are filtered based on the selected classes (cars and buses).
- Bounding boxes, labels, and tracking traces are annotated on the video.
- The line used for counting is also annotated, and the count of vehicles crossing the line is displayed.
- The annotated frames are saved into a new video file (toll_gate-result.mp4) in assets folder.

## Customization
- Vehicle Classes: Modify the `selected_classes` list to include other vehicle types based on YOLO's class indices.
- Counting Line Position: Adjust the coordinates of `LINE_START` and `LINE_END` to reposition the counting line in the video.

## Results
The output video will display:
- Detected vehicles with bounding boxes and labels.
- Tracking traces showing the movement of vehicles.
- A counter indicating the number of vehicles that have crossed the defined line.

## Acknowledgements
- YOLOv8 by Ultralytics for object detection.
- ByteTrack for tracking.
- Supervision library for annotating and managing detections.
