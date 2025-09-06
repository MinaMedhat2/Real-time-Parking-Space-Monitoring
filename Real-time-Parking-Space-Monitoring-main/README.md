# Real-time Parking Space Monitoring

This project implements a real-time parking space monitoring system using computer vision and machine learning.

---

## Overview

The system detects parking spots in a parking lot video and monitors their availability status (empty or occupied) in real time.

---

## How It Works

- The input is a video of a parking lot (`parking_1920_1080.mp4`) and a binary mask image (`mask_1920_1080.png`) that highlights parking spot locations.
- Using connected components analysis, the program identifies bounding boxes of individual parking spots.
- For each parking spot, a machine learning model predicts whether the spot is **empty** or **occupied** based on the image patch of that spot.
- The video frames are annotated with colored rectangles around each parking spot:
  - **Green**: Spot is available (empty)
  - **Red**: Spot is occupied
- The total number of available spots vs total spots is displayed on the video in real time.
- The output video window is shown in fullscreen mode without window borders.

---

## Components

- **Main script:** Processes the video frames, detects spots, and updates availability status.
- **Utility module (`util.py`):** Contains helper functions:
  - `get_parking_spots_bboxes`: Extracts bounding boxes of parking spots from the mask.
  - `empty_or_not`: Uses a trained machine learning model (`model.p`) to classify spots as empty or not.
- **Pre-trained model (`model.p`):** A machine learning classifier trained to distinguish empty vs occupied spots based on image patches.
- **Mask image (`mask_1920_1080.png`):** Highlights parking spots regions in the video frame.
- **Parking video (`parking_1920_1080.mp4`):** Input video to analyze.

---

## Requirements

- Python 3.x
- OpenCV (`cv2`)
- NumPy
- Matplotlib
- Scikit-image
- scikit-learn (for the model)
- Pickle (to load the pre-trained model)

Install dependencies via:

```bash
pip install opencv-python numpy matplotlib scikit-image scikit-learn
