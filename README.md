# posenet-reloc

Robot localization using [PoseNet](https://github.com/alexgkendall/caffe-posenet)

Keypoint-based camera localization (during SLAM or tracking) could fail in the presence severe appearance changes (day vs. night, sunny vs. rainy) and is sensitive to input quality, e.g. image resolution, sharpness and contrast. We intend to test the robustness of deep neural nets for stereo/monocular camera localization and pose estimation. PoseNet is a modification of GoogleNet to regress the 6-DOF camera pose which is described in this paper:

Alex Kendall, Matthew Grimes and Roberto Cipolla "[PoseNet: A Convolutional Network for Real-Time 6-DOF Camera Relocalization](http://arxiv.org/abs/1505.07427)." Proceedings of the International Conference on Computer Vision (ICCV), 2015. 

#### Dependencies:

 - [ROS](http://www.ros.org/) for extracting time-stamped left/right images and camera calibration from rosbags 
 - SLAM for automatic labeling of stereo input. We use [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2) 
 - [PoseNet](https://github.com/alexgkendall/caffe-posenet) for pose estimation from monocular vision (left camera)

#### Preparation of training data for PoseNet (automatic labeling):

To produce training labels (pose) from stereo vision, we use the keyboint-based [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2). 

Note: ORB-SLAM performs well in the absence of appearance changes. This allows us to extract accurate pose information from a single run. Meanwhile, training data for PoseNet can be a combination of multiple runs, each using ORB-SLAM to extract pose in a common coordinate system. 

Note: Structure From Motion can be used to extract pose from monocular vision if stereo is not available. 

Finally, we generate an LMDB database from the input images and the extracted pose labels.

#### Demo:

PoseNet estimating pose from the a single (left) camera after being trained over the same parking lot and the same day:

<a href="https://www.youtube.com/watch?v=oWsb1U0OkW8&feature=youtu.be" target="_blank"><img src="https://img.youtube.com/vi/oWsb1U0OkW8/0.jpg" alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

