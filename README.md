# ROS TurtleBot3 Integration

This task demonstrates the integration of the TurtleBot3 robot platform with the Robot Operating System (ROS) for robotic development and experimentation.

![image](https://github.com/ItsRawanMoha/ROS_Turtlebot3/assets/156599594/60f7b68a-8cbe-44ea-8d09-432d9def6532)

## Introduction

The TurtleBot3 is a popular open-source robot platform, it is widely used for learning robotics concepts, experimenting with ROS, and developing autonomous navigation algorithms.

## How it Works

The TurtleBot3 integrates hardware components such as a mobile base, sensors (e.g., LiDAR, cameras), and a compute module with ROS, a flexible framework for robotic software development. ROS provides libraries, tools, and conventions for building, simulating, and deploying robotic applications.
You can see in my previous task how we installed ROS.

## Getting Started

To get started with TurtleBot3 and ROS, you will need the following:

- TurtleBot3 robot platform (e.g., Burger, Waffle)
- Computer with Ubuntu Linux installed
- ROS ( Melodic) installed on the computer
- Simulation environment (e.g., Gazebo, RViz) for virtual testing and development


## Prerequisites
Before you start using TurtleBot3, ensure you have the following prerequisites installed:
- ROS: Follow the installation instructions at http://wiki.ros.org/ROS/Installation
- TurtleBot3 Packages: Install the necessary TurtleBot3 packages by following the instructions at https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup

## Steps

Follow these steps to integrate TurtleBot3 with ROS:

1. Install ROS on your computer following the official ROS installation instructions. (we did in previous task)
2. Configure the ROS environment and set up a catkin workspace for your ROS packages. (we did in previous task)
4. Install the TurtleBot3 ROS packages using the appropriate installation method (e.g., from source, via package manager).
5. Launch the necessary ROS nodes and controllers to control the TurtleBot3, visualize sensor data, and perform navigation tasks.

## Setting up

### Installing TurtleBot3 on Ubuntu operating system, Melodic version:

![image](https://github.com/ItsRawanMoha/ROS_Turtlebot3/assets/156599594/7d54e55a-4ed1-4449-bcf3-316e7108fdc2)

using these command on the terminal we successfully installed tutlebot3. 

## Simulation
### Install Simulation Package

```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
### Launch Simulation World

1- Empty World

![screen-gif](https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/VirtualBoxVM1.gif)

```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

2- TurtleBot3 World

![screen-gif](https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/VirtualBoxVM2.gif)

```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

3- TurtleBot3 House

![screen-gif](https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/VirtualBoxVM3.gif)

```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
NOTE: If TurtleBot3 House is launched for the first time, downloading the map may take more than a few minutes depending the network status!

### Operate TurtleBot3
In order to teleoperate the TurtleBot3 with the keyboard, launch the teleoperation node with below command in a new terminal window.
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

## SLAM Simulation

### Launch Simulation World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

### Run SLAM Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

### Run Teleoperation Node

```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

 Control Your TurtleBot3!
 ---------------------------
 Moving around:
        w
   a    s    d
        x

 w/x : increase/decrease linear velocity
 a/d : increase/decrease angular velocity
 space key, s : force stop

 CTRL-C to quit
```
![screen-gif](https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/VirtualBoxV4.gif)

### Save Map

![screen-gif](https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/map.png)

```
$ rosrun map_server map_saver -f ~/map
```

## Navigation Simulation

### Launch Simulation World

```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

### Run Navigation Node

```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```

-Estimation Initial Pose and Set Navigation Goal

```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
<img src="https://github.com/ItsRawanMoha/ROS_Turtlebot3/blob/main/VirtualBox5.gif" alt="Alt text" width="800" height="700">  

## Output

Once the TurtleBot3 is successfully integrated with ROS and the necessary nodes are launched, you can see and develop autonomous navigation algorithms using ROS tools and libraries.

## Conclusion

Integrating TurtleBot3 with ROS provides a powerful platform for learning robotics, experimenting with ROS concepts, and developing advanced robotic applications. By leveraging the capabilities of ROS and the flexibility of TurtleBot3, developers can explore a wide range of robotics tasks and research topics.
