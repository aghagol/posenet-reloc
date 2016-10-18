# DCN-nav
Robot localization using [PoseNet](https://github.com/alexgkendall/caffe-posenet)

Keypoint-based camera localization (during SLAM or tracking) could fail in the presence severe appearance changes (day vs. night, sunny vs. rainy) and is sensitive to input quality, e.g. image resolution, sharpness and contrast. We intend to test the robustness of deep nets, such as PoseNet, for stereo/monocular camera localization and pose estimation.

#### Preparation of training data for PoseNet (automatic labeling):

To produce training labels (pose) from stereo vision, we use the keyboint-based [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2). 

Note: ORB-SLAM usually performs well in the absence of appearance changes. This allows us to extract accurate pose information from a single run. Meanwhile, training data for PoseNet can be a combination of multiple runs, each using ORB-SLAM to extract pose in a common coordinate system. 

Note: Structure From Motion can be used to extract pose from monocular vision if stereo is not available. 

Finally, we generate an LMDB database from the input images and the extracted pose labels.

#### Stereo-PoseNet:

PoseNet uses monocular input by default. Can we improve PoseNet's accuracy using stereo vision? 

We test two ways of making PoseNet stereo: 

 - Combine 2 PoseNets using the Siamese architecture
 
 - Feed a single PoseNet with the stereo vision that is embedded in a multi-channel tensor
 
#### Demos:

[Monocular pose estimation using PoseNet](https://youtu.be/oWsb1U0OkW8)
