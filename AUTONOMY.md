# Previous Systems
- [Previous project board](https://github.com/orgs/SC-Robotics-2021/projects/5)
- [osiris hardware](https://github.com/SC-Robotics-2021/osiris_hardware)
- [osiris_autonomy](https://github.com/SC-Robotics-2021/osiris_autonomy)
- [ ] [Josh's legacy Valk's documentation on General System and Performances](https://github.com/SC-Robotics-2021/systems_documentation/tree/master/valkyrie_src)
- [ ] [Osiris's documentation and System](https://github.com/SC-Robotics-2021/systems_documentation/tree/master/osiris_src)

# Stuff to Look Into For New System
- [NVIDIA Isaac AMR Platform](https://www.nvidia.com/en-us/deep-learning-ai/industries/robotics/autonomous-mobile-robots/)
- [NVIDIA Isaac ROS](https://developer.nvidia.com/isaac-ros)
- [NVIDIA Isaac Sim](https://developer.nvidia.com/isaac-sim)
- [NVIDIA Keynote](https://youtu.be/PWcNlRI00jo)
- [NVIDIA Jetpack for Xavier](https://developer.nvidia.com/embedded/jetpack)
- [NVIDIA ROS2 Jetson](https://nvidia-ai-iot.github.io/ros2_jetson/)
- [Latest ZED ROS2 Wrapper](https://github.com/stereolabs/zed-ros2-wrapper)
- PID Loop
- QR code -> OpenCV -> croods -> vectors (nav2)
- SLAM and VSLAM

# New System Notes
### ROS2
- Using ROS2 Architecture and Python to speak with Raspberry PIs and other sensors.
### NVIDIA Jetson
- NVIDIA Jetson: Embedded computing board designed for AI computations. (Current: NVIDIA Jetson AGX Xavier)
- NVIDIA Jetpack: SDK for development.
- NVIDIA Jetson Linux: OS for Jetson.
### ZED Camera
- Stereolabs ZED camera: Camera for depth sensing and AI application. Has many other sensors built in.
- For ZED camera to work with ROS2: ZED ROS2 Wrapper.

# Autonomy Goal Notes:
Rover will have a starting gps coordinate.
Rover to move to given gps coordinate.
Read AR codes along path to find next gps coordinates.
Need to avoid obstacles and have dynamic drive system. But generally stay on path to next gps coordinate.

# Comments
- Osiris's implementation was with using ros2 while Valk's system was a bit barebone. Need to investigate and integrate both systems into 1 or start fresh.

# Steps to set up Jetson AGX Xavier for Autonomy
### The following instructions are to be completed on an x86 computer w/ ubuntu 16.04,18.04, or 20.04
1. Install [Jetson SDK Manager](https://developer.nvidia.com/nvidia-sdk-manager)
2. Use Jetson SDK Manager to flash Jetson Xavier with [JetPack 5.0.2 SDK manager](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html)
  *note: Jetson should be connected to computer w/ SDK manager installed, presumably over USB-C
	*note: JetPack 5.0.2 uses Jetson Linux, which has an Ubuntu 20.04 Desktop environment file system. This should hopefully play well with ROS2
  *note: JetPack 5.0.2 documentation says Jetpack includes CUDA 11.4. This should hopefully play well with ZED and ROS2
### The following instructions are to be completed on the Jetson Xavier
3. install ZED SDK for L4T 35.1 (Jetpack 5.0) 3.7.7 to allow use of ZED camera by jetson [link](https://www.stereolabs.com/developers/release/)
4. install [ROS2 Foxy Fitzroy](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html#)
5. install zed_ros2_wrapper using ROS2 colcon to allow ZED to be controlled by ROS2 [link](https://www.stereolabs.com/docs/ros2/)
4. Visit NVIDIA Isaac ROS's github to find packages for different autonomy systems [link](https://github.com/NVIDIA-ISAAC-ROS)

### Tutorial to help with install
(for step 2) Install [Jetson Software with SDK Manager](https://www.stereolabs.com/developers/release/)
(for step 3) Install [ZED SDK on Nvidia Jetson](https://www.stereolabs.com/docs/installation/jetson/)
