|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

# Gazebo installation

First, install Gazebo Garden with the instructions given in the link below.

[Gazebo Garden Binary Install](https://gazebosim.org/docs/garden/install_ubuntu#binary-installation-on-ubuntu)

Then install the corresponding rosdep rules.

[*Gazebo Garden *](https://github.com/osrf/osrf-rosdep#installing-rosdep-rules-to-resolve-gazebo-garden-libraries)[*R*](https://github.com/osrf/osrf -rosdep#installing-rosdep-rules-to-resolve-gazebo-garden-libraries)[*osdep *](https://github.com/osrf/osrf-rosdep#installing-rosdep-rules-to-resolve-gazebo-garden-libraries)[*R*](https://github.com/osrf/osrf -rosdep#installing-rosdep-rules-to-resolve-gazebo-garden-libraries)[*ules*](https://github.com/osrf/osrf-rosdep#installing-rosdep-rules-to-resolve-gazebo -garden-libraries)

Finally, clone the ros_gz packages in your workspace and build them. Make sure to compile it for `GZ_VERSION=garden`.

[*Installing ros_gz *](https://github.com/gazebosim/ros_gz/tree/humble#from-source)[*F*](https://github.com/gazebosim/ros_gz/tree/humble#from-source)[ *rom *](https://github.com/gazebosim/ros_gz/tree/humble#from-source)[*S*](https://github.com/gazebosim/ros_gz/tree/humble#from-source)[ *source*](https://github.com/gazebosim/ros_gz/tree/humble#from-source)

You can use the following command to prevent your RAM from suddenly filling up. It will take about 10 minutes to compile depending on your hardware.

```shell
MAKEFLAGS="-j2"; colcon build --parallel-workers 1 --symlink-install
--packages-select ros_gz ros_gz_bridge ros_gz_image ros_gz_interfaces
ros_gz_sim ros_gz_sim_demos
```

# Exercise 1

Activate the workspace where you created ros_gz. To test Gazebo installation, follow the link below and open shapes.sdf.

[Getting Started](https://gazebosim.org/docs/garden/getstarted)

If you encounter errors related to QT plugins, clear the QT environment variables before running Gazebo.

# Exercise 2

Follow the link below to create a bridge between ROS2 and Gazebo.

[ROS2 Integration] (https://gazebosim.org/docs/garden/ros2_integration)
