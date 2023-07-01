[toc]

# Environment Configuration

## qpOASES

We use qpOASES to solve MPC，and MPC is used for trajectory tracking

qpOASES  solver installation :

```bash
cd qpOASES
mkdir build
 cd build
 cmake ..
 sudo make
 sudo make install
```

## patchwork

patchwork is used for ground segmentation. This planner accepts 3d point cloud information **Pointcloud2**. After the point cloud is segmented on the ground, the point cloud is projected to the 2d plane to construct a 2d grid map for planning.

The repo has a version of patchwork, so you don't need to download it again.
Its official repository：[patchworl_github](https://github.com/LimHyungTae/patchwork)

## Simulation environment

The simulation environment uses the open source simulation environment of the CMU Robotics Institute. Users  need to install the relevant libraries and download the mesh file. We recommend to use the indoor environment to test the planner.

The environment have two versions for ros-melodic and ros-noetic. The package contained in this project is for ros-melodic.
So you don't need to download it again if you use ros-melodic.
Actually, we also successfully built and ran this repo on ros noetic + ubuntu 20.04.
[CMU-environment](https://www.cmu-exploration.com/)

# Build
```
catkin build
```

# Quick Start

First , start the simulation environment :

```bash
roslaunch vehicle_simulator system_indoor.launch
```

If you want to other environments say the garage, you need to comment out the planners from system_garage.launch as done with system_indoor.launch.

Second, start the planner :

```bash
roslaunch ego_planner run_in_sim.launch
```

In rviz , use  **2d nav goal** to set the goal :

![ego example](imag/ego example.gif)

If you can't see the imag in this file, you can see it in the folder "imag".

# THANKS

We are very grateful for Fei Gao and the EGO-Planner he proposed. Our algorithm is implemented under their algorithm framework. If you are interested in our algorithm, you may see the origin algorithm in :

[EGO-Planner](https://github.com/ZJU-FAST-Lab/ego-planner)

