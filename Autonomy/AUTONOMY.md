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
-[Software and Hardware Stack Compatibility Matrix](https://docs.google.com/spreadsheets/d/1t-nCCwkkZQgr5q8uTV1uusqkHtPhM9K14CyHfFUXnlk/edit?usp=sharing)
## Temp software list for NVIDIA ISAAC ROS
 - https://github.com/NVIDIA/nvidia-docker
 - https://developer.nvidia.com/cuda-downloads
### ROS2
- Using ROS2 Architecture and Python to speak with Raspberry Pis and other sensors.
- Using ROS2: Humble.
### NVIDIA Jetson
- NVIDIA Jetson: Embedded computing board designed for AI computations. (Current: NVIDIA Jetson AGX Orin)
- NVIDIA Jetpack: SDK for development.
- NVIDIA Jetson Linux: OS for Jetson.
### ZED Camera
- Stereolabs ZED2i camera: Depth camera, has IMU and gyro.
### Intel RealSense Camera
- (Full Camera Name): Depth camera, (list sensors).
### NVIDIA ISAAC ROS2 Autonomy Packages
- Packages to help with autonomy. AprilTags, VSLAM, etc.
### GPS
- (List GPS Name)
### Lidar
- RPLidar (Find full name)
- Measures distances around the sensor.
### Raspberry Pis
- Mini computer.
- Have a Pi for each system to easily swap out if breaks.
- OS: Ubuntu Server or Raspberry Pi OS (Raspbian). (Depending on use of Pi)

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
- note: Jetson should be connected to computer w/ SDK manager installed, presumably over USB-C
- note: JetPack 5.0.2 uses Jetson Linux, which has an Ubuntu 20.04 Desktop environment file system. This should hopefully play well with ROS2
- note: JetPack 5.0.2 documentation says Jetpack includes CUDA 11.4. This should hopefully play well with ZED and ROS2
### The following instructions are to be completed on the Jetson Xavier
3. install [ZED SDK for L4T 35.1 (Jetpack 5.0) 3.7.7](https://www.stereolabs.com/developers/release/) to allow use of ZED camera by jetson
6. Install [docker](https://docs.docker.com/engine/install/ubuntu/), check if already installed first
4. install [ROS2 Foxy Fitzroy](https://github.com/dusty-nv/jetson-containers#ros-containers) docker container
- note: it seems like Nvidia Isaac might require ROS2 humble, more details below. If you're not sure yet how to proceed, this would be a good time to pause and discuss. [This Forum](https://answers.ros.org/question/341372/can-nodes-from-different-ros-2-distributions-communicate-compatibly/) from a ROS dev says that while you may be able to communicate with different nodes across distrubutions as long as the protocols and messages are the same, this is not supported and should not be relied on. This means our entire robot should most likely either run on Foxy or Humble, however it seems that Nvidia Isaac can only run on Humble. So, it seems are options are: upgrade the entire system to humble, just run the Jetson on humble and try to let it communicate, or search for another AI library/older releases of Isaac that support foxy.
5. install [zed_ros2_wrapper](https://www.stereolabs.com/docs/ros2/) using ROS2 colcon to allow ZED to be controlled by ROS2
6. Add external storage device to jetson to give it at least 30GB of capacity (necessary for Isaac ROS Development Environment)
7. Set up [Isaac ROS Development Environment](https://github.com/SC-Robotics-2021/valk_2022-23/edit/master/AUTONOMY.md)

### Tutorial to help with install
- (for step 2) Install [Jetson Software with SDK Manager](https://www.stereolabs.com/developers/release/)
- (for step 3) Install [ZED SDK on Nvidia Jetson](https://www.stereolabs.com/docs/installation/jetson/)

### Useful Repos from [NVIDIA Isaac ROS's github](https://github.com/NVIDIA-ISAAC-ROS), and support for said repos
- [ROS2 Support on NVIDIA Jetson](https://nvidia-ai-iot.github.io/ros2_jetson/) this document has lots of links on jetson support. It says everything is compatible with ros2 foxy, however the repos linked contradict this. My guess is when NVIDIA updated their repos to support NITROS hardware acceleration, they used features in Humble not availible in Foxy. I believe this website is out of date, and Nvidia Isaac no longer supports Foxy
- [Apriltag](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_apriltag) Detect AprilTag images, VERY useful for rover project. ONLY supported by ROS2 Humble
- [Argus Camera](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_argus_camera) Allows use and data transfer of cameras. ONLY supported by ROS2 Humble
- [NITROS](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_nitros) Hardware acceleration, only availible w/ ROS2 Humble
