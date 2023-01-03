# Autonomy Documentation

## Previous Systems
- [Previous project board](https://github.com/orgs/SC-Robotics-2021/projects/5)
- [osiris hardware](https://github.com/SC-Robotics-2021/osiris_hardware)
- [osiris_autonomy](https://github.com/SC-Robotics-2021/osiris_autonomy)
- [Josh's legacy Valk's documentation on General System and Performances](https://github.com/SC-Robotics-2021/systems_documentation/tree/master/valkyrie_src)
- [Osiris's documentation and System](https://github.com/SC-Robotics-2021/systems_documentation/tree/master/osiris_src)

## Useful Links
- [NVIDIA Isaac AMR Platform](https://www.nvidia.com/en-us/deep-learning-ai/industries/robotics/autonomous-mobile-robots/)
- [NVIDIA Isaac ROS](https://developer.nvidia.com/isaac-ros)
- [NVIDIA Isaac Sim](https://developer.nvidia.com/isaac-sim)
- [NVIDIA Keynote](https://youtu.be/PWcNlRI00jo)
- [NVIDIA Jetpack for Xavier](https://developer.nvidia.com/embedded/jetpack)
- [NVIDIA ROS2 Jetson](https://nvidia-ai-iot.github.io/ros2_jetson/)
- [Latest ZED ROS2 Wrapper](https://github.com/stereolabs/zed-ros2-wrapper)
- [Isaac SDK Documentation](https://docs.nvidia.com/isaac/doc/index.html)

## New System Notes
- [Software and Hardware Stack Compatibility Matrix](https://docs.google.com/spreadsheets/d/1t-nCCwkkZQgr5q8uTV1uusqkHtPhM9K14CyHfFUXnlk/edit?usp=sharing)

## Temp software list for NVIDIA ISAAC ROS
- https://github.com/NVIDIA/nvidia-docker
- https://developer.nvidia.com/cuda-downloads

## ROS2
- Using ROS2 Architecture and Python to speak with Raspberry Pis and other sensors.
- Using ROS2 version: Humble.

## On-board Computer
- Model: NVIDIA Jetson AGX Orin 32 GB
- NVIDIA Jetson: Embedded computing board designed for AI computations and robotics.
- Our Dev Kit: 
- NVIDIA Jetpack: SDK for development.
- NVIDIA Jetson Linux: OS for Jetson.

## Stereo Camera
- Model: Stereolabs Zed2i
- Allows for depth perception, imu, temperature sensors, gyro.
- Out model does not have polarized lens.

## Nvidia Isaac Ros Packages
- [Isaac Ros Repos](https://github.com/NVIDIA-ISAAC-ROS)
- Ros2 packages to help with autonomy.
- Packages in-use:
  - [Isaac Ros Visual SLAM](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_visual_slam)
  - [Isaac Ros Proximity Segmentation](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_proximity_segmentation)
  - ...

## GPS
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

# Setting up Nvidia software and drivers for testing on a PC / Laptop
- Need Nvidia GPU
- Install nvidia-docker2: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html
  - If you get an error 'cannot find nvidia runtime' while attempting to connect nvidia docker (ex: testing Isaac packages), do these commands.

        sudo apt install -y nvidia-docker2
        sudo systemctl daemon-reload
        sudo systemctl restart docker
  
- Install Nvidia cuda toolkit: https://developer.nvidia.com/cuda-toolkit
  - I do not recommend installing cuda toolkit directly from apt, I was having problems.
  - **Nvidia cuda toolkit I think also will install the nvidia driver, so you may not need to manually install driver.**
- To manually install driver:
  - Check for driver: 

        ubuntu-drivers devices
        sudo apt install nvidia-<driver number>
       
  - Use latest driver. (Recommended driver was broken for me. I used the non-open driver because open was not letting Ubuntu shutdown correctly, and was not getting hdmi output for external screen).
  - Make sure to restart after installing drivers!
- Check these things:
  - Make sure the application 'Nvidia X Server' shows your GPU name and info.
  - Make sure you can run `nvidia-smi` command in terminal. It should show you driver info.
- If you are in a situation where you need to remove all nvidia drivers and tools, run these commands, then reboot:

      sudo apt-get remove --purge '^nvidia-.*'
      sudo apt-get remove --purge '^libnvidia-.*'
      sudo apt-get remove --purge '^cuda-.*'
- If you ever get a cmake error `Specify CUDA_TOOLKIT_ROOT_DIR` or having to do with `CUDA`, the Nvidia driver or the cuda toolkit is probably not installed correctly.
