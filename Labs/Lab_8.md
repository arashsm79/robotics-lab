|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

In this lab, we are going to add a LIDAR sensor to the mobile robot designed in the previous experiment. This sensor finds the distance to objects and can be used, for example, to make a map of the environment.

# Exercise 1

Add a LIDAR sensor to the previous robot mobile using [this tutorial](https://gazebosim.org/docs/garden/sensors#lidar-sensor). Add this model to the `maze.sdf` world, making sure to add the relevant plugins and reduce the physical size of the model so that it fits easily in the world. 

# Exercise 2

Bridge the `/lidar` topic using [ros_gz_bridge](https://github.com/gazebosim/ros_gz/tree/ros2/ros_gz_bridge). Run rviz2 and add a LaserScan display. Specify the sensor topic and make sure the simulation is running.  Are the points related to LaserScan visible?

Run the following command in a separate terminal:

``` shell
$ ros2 run tf2_ros static_transform_publisher "0" "0" "0" "0" "0" "0" "world" "vehicle_blue/chassis/gpu_lidar"
```

Run rviz again and repeat the previous steps. Are the points related to the sensor visible this time? Why?

# Exercise 3

Write a ROS2 package  that uses [ros_gz_bridge](https://github.com/gazebosim/ros_gz/tree/ros2/ros_gz_bridge) to bridge the topics related to Twist and LaserScan between Gazebo and ROS2 and drives the robot using them. If the robot gets too close to a wall, it should back off a bit, change directions, and then start moving forward again. Use the `maze.sdf` world and write a launch file to run your bridge and node.
