# SFND 2D Feature Tracking

# Student Results

## MP1 Ring Buffer
I implemented this by using a fixed size vector and assigning new frames to vector[frame_num % buffersize]

## MP2 Keypoint Detection
Done using create() interface shared amongst all subclasses

## MP3 Keypoint Removal
Done using Rect.contains

## MP4 Descriptors
Done 

## MP5 Flann Matching
Done

## MP6 Distance Ratio
If best_match_distance / second_best_match_distance >= 0.8, reject point

## MP7 Performance Evaluation 1
Done in sheet called "Detector Stats MP7" https://docs.google.com/spreadsheets/d/1vu_TOSerAiDMfBvoAezOFrgu4kW6wQn5C60M_KKCrLc/edit?usp=sharing

## MP8 + MP 9 Performance Evaluations
MP8 Done in sheet _MATCH STATS + TIME MP8 + MP9_ column D
MP9 in same sheet, column G

# Recommend detector/descriptor combos:

## Highest Number of matched points:
1.  Fast + SIFT, this pair had a large number of matches (2.8k over all frames), and found matches for about 70% of its proposed keypoints. 

## Good mix of accuracy and speed:
2. Fast + BRIEF or FAST + ORB had  similar matching performance and ran in half the time when compared to FAST + SIFT

## Best ratio for matches
3. AKAZE + SIFT had the highest keypoint match score, with 76% of keypoints matched over all frames, it was also 2x slower than Fast + SIFT. It is also the only combo that had keypoint stddev > 0, which might make this combo better when scale changes are occuring. 


# End of Student Report

<img src="images/keypoints.png" width="820" height="248" />

The idea of the camera course is to build a collision detection system - that's the overall goal for the Final Project. As a preparation for this, you will now build the feature tracking part and test various detector / descriptor combinations to see which ones perform best. This mid-term project consists of four parts:

* First, you will focus on loading images, setting up data structures and putting everything into a ring buffer to optimize memory load. 
* Then, you will integrate several keypoint detectors such as HARRIS, FAST, BRISK and SIFT and compare them with regard to number of keypoints and speed. 
* In the next part, you will then focus on descriptor extraction and matching using brute force and also the FLANN approach we discussed in the previous lesson. 
* In the last part, once the code framework is complete, you will test the various algorithms in different combinations and compare them with regard to some performance measures. 

See the classroom instructipon and code comments for more details on each of these parts. Once you are finished with this project, the keypoint matching part will be set up and you can proceed to the next lesson, where the focus is on integrating Lidar points and on object detection using deep-learning. 

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.