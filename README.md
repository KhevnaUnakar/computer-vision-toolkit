# Computer Vision Toolkit: Image Processing, Feature Extraction & Object Detection

A Python-based computer vision project that explores image restoration, image segmentation, feature extraction, object detection, and motion estimation using OpenCV and other popular computer vision libraries.

The project demonstrates practical computer vision techniques through Jupyter Notebooks, visual outputs, and quantitative evaluation metrics.

## 📌 Project Overview

Computer vision enables computers to interpret and process visual information from images and videos. This project implements fundamental computer vision algorithms and compares their results to understand their applications, strengths, and limitations.

## 🎯 Objectives

- Apply image restoration techniques to images corrupted by different types of noise.
- Perform image segmentation using thresholding, morphological operations, edge detection, and watershed segmentation.
- Extract and compare image features using HOG and SIFT.
- Detect faces and objects using Haar Cascade classifiers and YOLO.
- Explore motion estimation techniques on video footage using frame differencing, background subtraction, and optical flow.

## 🛠️ Technologies Used

- **Python** — Core programming language
- **OpenCV** — Image processing, feature detection, object detection, and video analysis
- **NumPy** — Numerical operations and array manipulation
- **Matplotlib** — Visualization of images and results
- **scikit-image** — HOG feature extraction and image quality metrics
- **Ultralytics YOLO** — Deep-learning-based object detection
- **Jupyter Notebook** — Interactive development and experimentation

## 📂 Project Structure

```text
ComputerVisionToolkit/
├── data/
│   ├── images/
│   │   └── original.jpeg
│   ├── videos/
│   │   └── original_video.mp4
│   └── haarcascades/
│       └── haarcascade_frontalface_default.xml
├── notebooks/
│   ├── 01_image_restoration.ipynb
│   ├── 02_segmentation.ipynb
│   ├── 03_feature_extraction.ipynb
│   ├── 04_object_detection.ipynb
│   └── 05_motion_estimation.ipynb
├── outputs/
│   ├── restoration/
│   ├── segmentation/
│   ├── features/
│   ├── detection/
│   └── motion/
├── requirements.txt
├── .gitignore
└── README.md
```

*Note: The motion estimation notebook and its outputs are planned/in progress. Update this section as the project develops. The image, video, and Haar Cascade filenames should match the files used in your local setup.*

## 🔍 Modules and Implementation

### 1. Image Restoration

This module examines how noise affects image quality and evaluates filtering methods for restoring images.

**Implemented techniques:**
- Gaussian noise addition
- Salt-and-pepper noise addition
- Gaussian Blur
- Median Blur
- Peak Signal-to-Noise Ratio (PSNR)
- Structural Similarity Index (SSIM)

**Evaluation:**

| Noise Type | Restoration Method | PSNR (dB) | SSIM |
|---|---|---:|---:|
| Gaussian | Gaussian Blur | 30.55 | 0.7486 |
| Gaussian | Median Blur | 31.61 | 0.7685 |
| Salt-and-pepper | Gaussian Blur | 29.39 | 0.7022 |
| Salt-and-pepper | Median Blur | 40.64 | 0.9744 |

**Observation:** Median Blur performed particularly well for salt-and-pepper noise, achieving a PSNR of 40.64 dB and an SSIM of 0.9744 in the tested image. It also performed slightly better than Gaussian Blur for the tested Gaussian-noise image.

### 2. Image Segmentation

This module separates image regions and highlights boundaries using classical image processing techniques.

**Implemented techniques:**
- Binary thresholding
- Adaptive thresholding
- Morphological erosion and dilation
- Morphological opening and closing
- Canny edge detection
- Watershed segmentation

The resulting images are saved in `outputs/segmentation/` for visual inspection and comparison.

### 3. Feature Extraction and Matching

This module explores local and gradient-based image features.

**Implemented techniques:**
- Histogram of Oriented Gradients (HOG)
- Scale-Invariant Feature Transform (SIFT)
- SIFT keypoint and descriptor extraction
- Brute-force feature matching
- Lowe's ratio test
- Feature matching after image rotation and resizing

The experiments help demonstrate how image features can be used to identify and match visual patterns across transformed images.

### 4. Object Detection

This module compares traditional cascade-based face detection with deep-learning-based object detection.

**Implemented techniques:**
- Haar Cascade frontal-face detection
- YOLO object detection using the Ultralytics library
- Bounding-box visualization
- Predicted class labels and confidence scores

**Comparison:** Haar Cascade is designed for a specific detection task in this implementation—frontal-face detection. YOLO can detect multiple object categories supported by its pretrained model. Their outputs can be compared based on detected objects, localization, and confidence scores.

### 5. Motion Estimation *(In Progress)*

This module is intended to analyze movement in a self-recorded video.

**Planned techniques:**
- Frame differencing
- Background subtraction using a Gaussian Mixture Model (GMM)
- Lucas–Kanade optical flow

The outputs will be used to compare how the techniques identify moving objects and estimate motion across video frames.

## 📊 Outputs

The project stores generated visualizations and experiment results in the `outputs/` directory.

Examples include:

- Noisy and restored images
- Image segmentation and edge maps
- HOG visualizations and SIFT keypoints
- Feature-matching visualizations
- Haar Cascade and YOLO detection results
- Motion estimation results *(once implemented)*

## ⚙️ Setup and Installation

### Prerequisites

- Python 3.10 or another Python version compatible with the selected dependencies
- pip
- Jupyter Notebook
- Git

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/ComputerVisionToolkit.git
cd ComputerVisionToolkit
```

Replace `YOUR-USERNAME` with your GitHub username and adjust the repository name if needed.

### 2. Create a virtual environment

**Windows:**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the notebooks inside the `notebooks/` directory and execute the cells in sequence.

## 🖼️ Input Data

The project uses an original image and a self-recorded video as input data.

- Place the image in `data/images/`.
- Place the video in `data/videos/`.
- Ensure that the paths in the notebooks match the actual filenames.

The Haar Cascade XML file should be available at `data/haarcascades/haarcascade_frontalface_default.xml` if using the configured local path.

**YOLO model:** The pretrained `yolov8n.pt` weights may be downloaded automatically by Ultralytics when the model is initialized, depending on the environment and network access.

## 📈 Evaluation and Analysis

The project combines visual inspection with quantitative evaluation where applicable.

- **PSNR:** Measures reconstruction quality relative to the original image; higher values generally indicate lower pixel-level error.
- **SSIM:** Measures structural similarity between images; values closer to 1 generally indicate greater similarity.
- **Feature matching:** Examines correspondences between an original image and rotated or resized versions.
- **Object detection:** Examines predicted classes, bounding boxes, and confidence scores.
- **Motion estimation:** Will compare detected changes and estimated motion across video frames.

Results may vary depending on the input image, video, parameter settings, and library versions.

## 🚀 Future Improvements

- Add more image restoration filters and compare their performance.
- Experiment with different segmentation parameters and input images.
- Evaluate feature matching under additional transformations.
- Compare object detection performance across different images and model configurations.
- Complete and compare the motion estimation methods.
- Add a consolidated results report with screenshots and observations.

## 👩‍💻 Author

**Khevna Unakar**

MCA Student | Computer Vision | Software Development

## 📄 License

This project was developed for educational and academic purposes. Add a specific open-source license if you intend to permit reuse or redistribution under defined terms.
