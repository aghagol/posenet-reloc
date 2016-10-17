# DCN-nav
Stereo vision-based Robot Localization using [PoseNet](https://github.com/alexgkendall/caffe-posenet)

Keypoint-based camera localization (during SLAM or tracking) could fail in the presence severe appearance changes (day vs. night, sunny vs. rainy) and is sensitive to input quality, e.g. image resolution, sharpness and contrast. We intend to test the robustness of deep nets, such as PoseNet, for stereo/monocular camera localization and pose estimation.

#### Preparation of training data for PoseNet:

To get training labels (pose) from stereo vision, we use the keyboint-based [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2). 

Note: ORB-SLAM usually performs well in the absence of extreme appearance changes. This allows us to extract accurate pose information from a single run. Training data for PoseNet can be a combination of multiple runs, each using ORB-SLAM to extract pose in a common coordinate system. 

An LMDB database is built from the input images and the extracted pose labels.

#### PoseNet variations:

PoseNet uses monocular input by default. Can we improve PoseNet accuracy using stereo vision? 

We take two approaches to test this: 

 - Modify PoseNet using the Siamese architecture
 
 - Embed stereo vision in a multi-channel tensor 
 
 
