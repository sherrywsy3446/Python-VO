# Task 1: Python Programming for Visual Odometry

## Overview

This project implements and evaluates Visual Odometry (VO) algorithms using Python in Jupyter notebooks. The project consists of two main components:

1. **Robustness Evaluation of Visual Odometry** - Testing VO performance under various image noise conditions
2. **Visual Odometry on PuzzleBot** - Implementation of VO on videos captured using a PuzzleBot robot

## Project Structure

```
.
├── task1.ipynb          # Robustness evaluation notebook
├── task2.ipynb          # Camera calibration and PuzzleBot VO notebook
├── Python-VO/utils/               # Utility functions and classes
│   ├── PinholeCamera.py # Camera model implementation
│   └── tools.py         # Helper functions
├── Python-VO/Detectors/           # Feature detection implementations
│   └── superpoint/      # SuperPoint detector
├── Python-VO/Matchers/            # Feature matching implementations
│   └── superglue/       # SuperGlue matcher
├── calibration_images/  # Images for camera calibration
│   └── calibration_result.yaml # Calibration parameters
├── results/             # Output directory for results
└── README.md            # This file
```

## Part 1: Robustness Evaluation of Visual Odometry

### Implemented in: `task1.ipynb`

This notebook evaluates how visual odometry performance degrades under different types and levels of image noise.

#### Visual Odometry Implementation
- images in KITTI loading and preprocessing
- Feature detection with SuperPoint
- Feature matching with SuperGlue
- Motion estimation using Essential matrix

### Implemented Noise Types
- **Gaussian Noise** - Simulates electronic noise in imaging sensors
- **Salt & Pepper Noise** - Simulates dead pixels or transmission errors
- **Speckle Noise** - Simulates multiplicative noise common in radar imaging


### Key Functions
- `add_gaussian_noise()` - Adds Gaussian noise to images
- `add_salt_pepper_noise()` - Adds salt and pepper noise to images
- `add_speckle_noise()` - Adds speckle (multiplicative) noise to images
- `evaluate_vo_with_noise()` - Evaluates VO performance with different noise parameters
- `plot_results()` - Visualizes trajectory comparison and error metrics
- `plot_all_noise_comparisons()` - Creates comprehensive visualizations
- `generate_rmse_matrix()` - Produces tabulated results
- `run_all_evaluations()` - Orchestrates the complete evaluation process

### Evaluation Metrics
- **Absolute RMSE** - Overall trajectory error compared to ground truth
- **Relative RMSE** - Frame-to-frame motion error
- **Processing Time** - Computational efficiency under different noise conditions

## Part 2: Visual Odometry on PuzzleBot

### Implemented in: `task2.ipynb`

This notebook implements visual odometry on videos captured using the PuzzleBot robot with Jetson Nano.

### Main Components

#### Camera Calibration
- Chessboard pattern detection
- Camera intrinsic parameter estimation
- Distortion coefficient calculation
- Undistortion visualization

#### Visual Odometry Implementation
- Video loading and preprocessing
- Feature detection with SuperPoint
- Feature matching with SuperGlue
- Motion estimation using Essential matrix
- Trajectory tracking and visualization

### Key Functions
- `read_calibration_yaml()` - Loads camera calibration parameters
- `run_vo_on_video()` - Main function for running VO on video files
- `TrajPlotter` - Class for visualizing and saving trajectory data

## Usage Instructions
### Running the Notebooks
first install the required packages:in requirments.txt
then install the required model weights about the superpoint and superglue
in: https://github.com/sherrywsy3446/Python-VO.git 
place the whole python-vo folder in the same directory as the notebooks
1. **For Task 1 (Robustness Evaluation)**:
   - Open `task1.ipynb` in Jupyter Notebook
   - Run all cells to perform the complete evaluation
   - Adjust the `num_frames` parameter in the final cell to control evaluation length
   - Results will be saved in the `results` directory

2. **For Task 2 (PuzzleBot VO)**:
   - Place calibration images in the `calibration_images` directory
   - Open `task2.ipynb` in Jupyter Notebook
   - Run the calibration section first to generate calibration parameters
   - Update the video path to point to your captured video
   - Run the VO implementation section
   - Visualizations and trajectory data will be saved in the `results` directory

## Key Features
- Deep learning-based feature detection and matching
- Robust camera calibration for accurate pose estimation
- Comprehensive noise simulation and evaluation
- Real-world testing on mobile robot platform
- Extensive visualization and analysis
