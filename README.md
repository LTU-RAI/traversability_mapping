# Traversability Mapping and Motion Planning

This is a modified version of the original traversability_mapping that can be found [here](https://github.com/TixiaoShan/traversability_mapping).

This repository contains code for a traversability mapping and motion planning system for ROS compatible UGVs. The system takes in point cloud from a Velodyne VLP-16 Lidar and outputs a traversability map for autonomous navigation in real-time. A demonstration of the system can be found here -> https://www.youtube.com/watch?v=4pdBpeRGXmw


## Get Started

- Install [ROS](http://www.ros.org/install/).
- Install [OpenCV](https://docs.opencv.org/3.4.16/d7/d9f/tutorial_linux_install.html) (version 4.0 and newer will not work).


## Compile

You can use the following commands to download and compile the package.

```
cd ~/catkin_ws/src
git clone https://github.com/LTU-RAI/traversability_mapping.git
cd ..
catkin build -j1
```

When you compile the code for the first time, you need to add "-j1" behind "catkin build" for generating some message types. "-j1" is not needed for future compiling.

## Run the System (in simulation)

1. Run the launch file:

```
roslaunch traversability_mapping offline.launch
```

2. Play existing bag files:

```
rosbag play *.bag --clock
```

Notes: our system only needs /velodyne_points for input from bag files. However, a 3D SLAM method usually needs /imu/data.

## Ros topics 

### Subscribed Topics

```/spot/velodyne_points``` Velodyne point cloud, can be configured in launch file.

### Published Topics

```/elevation_pointcloud``` voxel point cloud of hight map with traversability data

```/occupancy_map_local``` occupancy map local to robot

```/occupancy_map_global``` global occupancy map 

## Cite *Traversability_Mapping*

Thank you for citing our paper if you use any of this code: 

```
@inproceedings{bayesian2018shan,
  title={Bayesian Generalized Kernel Inference for Terrain Traversability Mapping},
  author={Shan, Tixiao and Wang, Jinkun and Englot, Brendan and Doherty, Kevin},
  booktitle={In Proceedings of the 2nd Annual Conference on Robot Learning},
  year={2018}
}
```
