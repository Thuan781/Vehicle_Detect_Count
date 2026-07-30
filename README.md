# Vehicle Detect-Count

A project for detecting and counting vehicles (cars and buses) in images and video using OpenCV's Haar Cascade classifiers.

## Overview

This project demonstrates how to:
- Fetch and preprocess images from the web
- Apply image processing techniques (grayscale conversion, Gaussian blur, dilation, morphological transformations) to improve detection accuracy
- Use pretrained Haar Cascade classifiers to detect cars and buses in static images
- Detect and count vehicles frame-by-frame in a video, and write the annotated output to a new video file

## Features

- **Image preprocessing**: grayscale conversion, Gaussian blur (noise reduction), dilation, and morphological closing
- **Car detection**: uses a car Haar Cascade (`cars.xml`) to detect and count cars in an image
- **Bus detection**: uses a bus Haar Cascade (`Bus_front.xml`) to detect and count buses in an image
- **Video processing**: reads a video frame-by-frame, detects vehicles in each frame, draws bounding boxes, and writes the result to an output video (`result.avi`)

## Requirements

See `requirements.txt`. Install dependencies with:

```bash
pip install -r requirements.txt
```

## Project Structure / Required Files

Since Haar Cascade classifiers and video files aren't included in this notebook, you'll need to supply the following in the same directory as the notebook:

| File | Description |
|---|---|
| `cars.xml` | Haar Cascade classifier for car detection |
| `Bus_front.xml` | Haar Cascade classifier for bus (front view) detection |
| `Cars.mp4` | Sample input video for vehicle detection/counting |

Pretrained Haar Cascade XML files for cars and buses are commonly available from open-source repositories (e.g., search for "cars.xml haar cascade" and "Bus_front.xml haar cascade" on GitHub).

## Usage

Open and run `Vehicle_Detect_Count.ipynb` in Jupyter Notebook / JupyterLab / Google Colab. The notebook will:

1. Download a sample image from a URL and resize it
2. Convert the image to grayscale, blur it, dilate it, and apply morphological closing
3. Run the car cascade classifier on the processed image and draw bounding boxes around detected cars
4. Download a second sample image (bus) and run the bus cascade classifier on it
5. Process a local video (`Cars.mp4`) frame-by-frame, detect cars in each frame, and save the annotated result to `result.avi`

## How It Works

Haar Cascade classifiers are pretrained models that use edge/line/rectangle features to detect objects at various scales in an image. `cv2.CascadeClassifier.detectMultiScale()` scans the image at multiple scales and returns bounding rectangles for detected objects (cars, buses, etc.). Preprocessing steps like grayscale conversion, blurring, and morphological operations help reduce noise and improve detection accuracy.

## Notes

- Detection accuracy depends heavily on the quality of the Haar Cascade XML files used and the resolution/clarity of the input images or video.
- Haar Cascades can produce false positives/negatives; for more robust detection, consider modern deep learning-based object detectors (e.g., YOLO, SSD).

