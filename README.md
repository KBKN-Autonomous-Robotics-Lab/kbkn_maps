# kbkn_maps
Repository for managing SLAM maps used in Tsukuba Challenge and other projects.
## How to use
### 1. Build
**ROS1**
```bash
$ cd <your-ros1-workspace>/src
$ git clone https://github.com/KBKN-Autonomous-Robotics-Lab/kbkn_maps.git
$ catkin build
```

**ROS2**
```bash
$ cd <your-ros2-workspace>/src
$ git clone https://github.com/KBKN-Autonomous-Robotics-Lab/kbkn_maps.git
$ cd <your-ros2-workspace> && colcon build
```

### 2. Example of specifying a map in the launch file
**ROS1**
```xml
<arg name="map_file" value="$(find kbkn_maps)/maps/gazebo/orange_hosei/slam_toolbox/map.yaml"/>
```

**ROS2**
```xml
<arg name="map_file" value="$(find-pkg-share kbkn_maps)/maps/gazebo/orange_hosei/slam_toolbox/map.yaml"/>
```
