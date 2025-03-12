# RSLiDAR_FAST_LIO  
Modified from [FAST-LIO](https://github.com/hku-mars/FAST_LIO) for RoboSense lidars.    
Also referred to the code in [LiDAR_IMU_Init](https://github.com/hku-mars/LiDAR_IMU_Init).  

## 1 What modified  
### 1.1 config  
Added `robosense_airy.yaml` and `robosense_e1r.yaml`.  

### 1.2 preprocess
Added support for robosense point struct in `preprocess.h` and `preprocess.cpp`.

### 1.3 launch
Added `mapping_airy.launch` and `mapping_e1r.launch`.

## 2 Download  
Download the `RSLiDAR_FAST_LIO` as below. Since it contains the submodule `ikd_tree`, please also download the submodule by
```sh
git clone https://github.com/Lya-M1RA/RSLiDAR_FAST_LIO.git
cd RSLiDAR_FAST_LIO
git submodule init
git submodule update
```
or
```sh
git clone https://github.com/Lya-M1RA/RSLiDAR_FAST_LIO.git --recursive
```

## 3 Prerequisites  
### 3.1 Ubuntu and ROS
**Ubuntu >= 16.04**

For **Ubuntu 18.04 or higher**, the **default** PCL and Eigen is enough for FAST-LIO to work normally.

ROS    >= Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)

### 3.2 PCL && Eigen
PCL    >= 1.8,   Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).

Eigen  >= 3.3.4, Follow [Eigen Installation](http://eigen.tuxfamily.org/index.php?title=Main_Page).

```sh
sudo apt install libpcl-dev libeigen3-dev
```

### 3.3 livox_ros_driver
Follow [livox_ros_driver Installation](https://github.com/Livox-SDK/livox_ros_driver).

*Remarks:*
- Since the FAST-LIO must support Livox serials LiDAR firstly, so the **livox_ros_driver** must be installed and **sourced** before run any FAST-LIO luanch file.
- How to source? The easiest way is add the line ``` source $Livox_ros_driver_dir$/devel/setup.bash ``` to the end of file ``` ~/.bashrc ```, where ``` $Livox_ros_driver_dir$ ``` is the directory of the livox ros driver workspace (should be the ``` ws_livox ``` directory if you completely followed the livox official document).

## 4 IMU init pose
RoboSense Airy has an internal IMU. The transformation matrix from an Airy's lidar frame to its IMU frame is 
$$
\begin{bmatrix} 0 & -1 & 0 \\ -1 & 0 & 0\\ 0 & 0 & -1\end{bmatrix}
$$

## 5 More details
For more details, please refer to the original [README](https://github.com/Lya-M1RA/RSLiDAR_FAST_LIO/blob/main/README_ORIGIN.md) of FAST-LIO.