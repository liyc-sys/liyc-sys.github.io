---
title: "Video Stitching and Processing - Computational Photography Project"
excerpt: "CS445 Computational Photography project implementing video stitching, panorama generation, and foreground/background segmentation using homography transformations and RANSAC."
collection: portfolio
date: 2024-12-03
category: course-project
---

# Video Stitching and Processing - Computational Photography Project

**Course**: CS445 Computational Photography  
**University**: University of Illinois at Urbana-Champaign  
**Completed**: December 2024  
**Project Type**: Technical Implementation 

## Project Overview

This project explores advanced computational photography techniques through video manipulation and image stitching. The main focus is on a 30-second video from Jaipur, Northern India (900 frames), implementing correspondence using interest points, robust matching with RANSAC, homography computation, and background subtraction.

## Technical Implementation

### Core Techniques Implemented

* **Interest Point Detection & Matching**: SIFT feature extraction for establishing correspondences between frames
* **Robust Matching**: RANSAC algorithm for outlier removal and reliable homography estimation
* **Homography Transformation**: Projective transformation mapping between different image planes
* **Video Stitching**: Mapping multiple video frames onto a single reference plane
* **Background Subtraction**: Separating static background from moving foreground objects
* **Panorama Generation**: Creating wide-angle views from multiple overlapping frames

### Technical Challenges

* **Frame Registration**: Accurately mapping frames with minimal overlap using multi-stage homography
* **Blending Artifacts**: Managing seamless transitions between overlapping image regions
* **Background Modeling**: Robust estimation of static background from moving foreground elements
* **Coordinate Transformations**: Handling negative coordinates and large canvas sizes

## Project Implementation Details

### Frame Stitching Implementation
- **Reference Frame**: Frame 450 as the base plane
- **Target Frame**: Frame 270 mapped onto reference plane
- **Process**: SIFT feature extraction → RANSAC matching → Homography computation → Image warping
- **Output**: Merged image showing two overlapping video frames seamlessly stitched

*Frame stitching demonstration videos coming soon*

### Multi-Frame Panorama Generation
- **Key Frames**: [90, 270, 450, 630, 810]
- **Challenge**: Direct mapping between distant frames (90 and 450) with minimal overlap
- **Solution**: Two-stage homography composition (90→270→450)
- **Output**: Complete panoramic view of the scene

*Panorama generation demonstration videos coming soon*

### Video Projection to Reference Plane
- **Process**: Apply homography transformations to all 900 frames
- **Reference**: Frame 450 coordinate system
- **Intermediate Frames**: Map distant frames through nearest key frames
- **Output**: Complete video sequence projected onto single plane

**Video Demonstration:**
[Projecting All Frames to Reference Frame - CS445 Project5 Part3](https://www.bilibili.com/video/BV1D24y1f7qF/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

### Background Panorama Construction
- **Technique**: Temporal median filtering across multiple frames
- **Principle**: Background colors appear more frequently than transient foreground colors
- **Implementation**: Analyze color distribution for each pixel across video sequence
- **Output**: Clean panorama showing only static background elements

*Background panorama demonstration videos coming soon*

### Background Video Generation
- **Process**: Inverse homography mapping from panorama to each frame
- **Result**: Video sequence with all moving objects removed
- **Application**: Clean background plate for visual effects

**Video Demonstration:**
[Empty Street Background Video - CS445 Project5 Part5](https://www.bilibili.com/video/BV1Zd4y1r7Zt/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

### Foreground Segmentation
- **Method**: Pixel-wise comparison with background model
- **Thresholding**: Identify significant color differences from background
- **Output**: Video containing only moving foreground elements

**Video Demonstration:**
[Foreground Segmentation Video - CS445 Project5 Part6](https://www.bilibili.com/video/BV1uG4y1t7CE/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

## Advanced Features

### Extended Implementation
* **Background/Foreground Optimization**: Improved algorithms for better separation quality
* **Extended Video Width**: Generated wider street view by expanding canvas beyond original boundaries

**Video Demonstrations:**
[Optimized Background Video - CS445 Project5 Part9](https://www.bilibili.com/video/BV15Y411Z73S/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

[Optimized Foreground Video - CS445 Project5 Part9](https://www.bilibili.com/video/BV1184y1v7Fv/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

[Wider Street Extended View - CS445 Project5 Part12](https://www.bilibili.com/video/BV1B8411b7Cq/?share_source=copy_web&vd_source=d3812f4b8deaefff649e54aa7decd2e9)

## Project Videos Overview

All video demonstrations are integrated within their respective implementation sections above for better context and understanding of each technique's application.

## Technical Results

### Key Achievements

* **Accurate Homography Estimation**: Robust RANSAC implementation with optimal threshold tuning
* **Multi-Frame Stitching**: Successful panorama generation from 5 key frames with minimal artifacts
* **Background-Foreground Separation**: Clean segmentation of moving objects from static scene
* **Temporal Consistency**: Smooth video output maintaining coherent geometry across frames

### Performance Metrics

* **Feature Matching**: Average [X] SIFT matches per frame pair
* **RANSAC Inlier Ratio**: [X]% of matches surviving outlier rejection
* **Panorama Resolution**: [X]×[Y] pixels covering full scene extent
* **Processing Time**: [X] minutes for complete video processing

## Algorithm Implementation Details

### Homography Pipeline
```python
# Pseudo-code for homography estimation
sift_features = extract_sift_features(frame1, frame2)
matches = ratio_test(sift_features)
H, inliers = ransac_homography(matches, threshold=X)
warped_frame = cv2.warpPerspective(frame, H, canvas_size)
```

### Background Modeling
* **Method**: Temporal median/mode filtering per pixel
* **Robustness**: Handles occasional camera movement and lighting changes
* **Output**: Static background panorama with moving objects removed

## Tools and Technologies

* **Programming Language**: Python
* **Libraries**: OpenCV (cv2), NumPy, Matplotlib
* **Feature Detection**: SIFT (Scale-Invariant Feature Transform)
* **Video Processing**: FFmpeg for frame extraction and video generation
* **Development Environment**: Jupyter Notebook

## Learning Outcomes

This project provided comprehensive experience in:

* **Computer Vision Fundamentals**: Feature detection, matching, and geometric transformations
* **Robust Estimation**: RANSAC algorithm for outlier rejection
* **Projective Geometry**: Understanding homographies and perspective transformations
* **Video Processing**: Frame-by-frame manipulation and temporal analysis
* **Algorithm Implementation**: From theoretical concepts to working code

## Challenges and Solutions

* **Minimal Overlap Challenge**: Solved through multi-stage homography composition
* **Blending Artifacts**: Addressed using appropriate feathering and overlap handling
* **Memory Management**: Optimized canvas size and coordinate transformations
* **Parameter Tuning**: Systematic experimentation with RANSAC thresholds and blending weights

## Future Extensions

* **Real-time Processing**: Optimization for live video stitching applications
* **Advanced Blending**: Implementation of Laplacian pyramid blending
* **3D Reconstruction**: Extension to 3D scene reconstruction from video sequences
* **Mobile Application**: Adapting algorithms for mobile device cameras

---

*This portfolio entry showcases the complete implementation of the CS445 Video Stitching and Processing project. Video demonstrations will be updated upon Bilibili upload.*