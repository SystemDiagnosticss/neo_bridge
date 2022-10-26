# ros2-ros1_bridge

This repository contains the ROS publisher for ros2 ros1 bridge.

## Prerequisites
1. Ubuntu 20.04
2. Python 3.8
3. ROS Noetic
4. ROS Galactic

## Development

### Setup
Prepare catkin workspace and build code:

```
$ mkdir -p ros2-ros1_ws/src
$ cd ros2-ros1_ws/src
$ catkin_init_workspace
$ cd ..
$ catkin_make
```

Now you need to source the `setup.bash` created in ros2-ros1_ws/devel/ directory

```
$ source ~/ros2-ros1_ws/devel/setup.bash
```

It is recommended to add a corresponding line to .bashrc to source required environment automatically.


### Build

Clone `neo_bridge` repository into catkin_ws/src directory and execute `catkin_make` in the root of catkin workspace:

```
$ cd catkin_ws/src
$ git clone https://github.com/SystemDiagnosticss/neo_bridge.git
$ cd ..
$ catkin_make
```

### Start

Run ROS talker in Shell A:

```
$ source /opt/ros/noetic/setup.bash
$ source ~/ros2-ros1_ws/devel/setup.bash
$ roslaunch ros2-ros1_bridge neo_talker.launch
```

Run ros1_bridge under ROS and ROS2 environment in Shell B:

```
$ source /opt/ros/noetic/setup.bash
$ source /opt/ros/galactic/setup.bash
$ export ROS_MASTER_URI=http://localhost:11311
$ ros2 run ros1_bridge dynamic_bridge
```

Run ROS2 listener in Shell C:

```
$ source /opt/ros/galactic/setup.bash
$ ros2 run demo_nodes_cpp listener
```
