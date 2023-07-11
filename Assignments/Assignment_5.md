
|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

Gazebo tutorials from labs:
- [Spawn Urdf](https://gazebosim.org/docs/garden/spawn_urdf)
- [Ros 2 Integration](https://gazebosim.org/docs/garden/ros2_integration)
* [Understanding The Gui] (https://gazebosim.org/docs/garden/gui)
- [Manipulating Models](https://gazebosim.org/docs/garden/manipulating_models)
- [Building Your Own Robot] (https://gazebosim.org/docs/garden/building_robot)
- [Moving The Robot](https://gazebosim.org/docs/garden/moving_robot)
- [Sdf Worlds](https://gazebosim.org/docs/garden/sdf_worlds)
- [Sensors](https://gazebosim.org/docs/garden/sensors)

ROS2 tutorials from previous assignments:
- [URDF](https://docs.ros.org/en/humble/Tutorials/Intermediate/URDF/URDF-Main.html)(make sure you're comfortable reading xacro files)
- [Simulating a Robot with Gazebo](https://docs.ros.org/en/humble/Tutorials/Advanced/Simulators/Gazebo.html)


# Exercise 1

Clone the [arashsm79/eddiebot-ros](https://github.com/arashsm79/eddiebot-ros) repository into your ws. This repository contains packages that allow us to setup, run and simulate [Eddie robot ](https://www.youtube.com/watch?v=oAqHhUtAHmQ) using ROS2 and Gazebo. For the rest of the semester, you will need to pull the new changes of this repository from the source.
Make sure all dependencies are set with the following command:

```shell
$ rosdep install -r --from-paths src -i -y --rosdistro humble
```

Then, using colcon, build the `eddiebot_rviz` and `eddiebot_description` packages and make sure you have sourced your local ws. Run the following command in your ws:

```shell
$ ros2 launch eddiebot_rviz view_model.launch.py description:='True'
```


# Exercise 2

Build the `eddiebot_gazebo` package using colcon. Run the following command:

```shell
$ ros2 launch eddiebot_gazebo eddiebot_gz_sim.launch.py 'world:=maze_marked'
```

In Gazebo and from the top right menu, add the Teleop module and put the following text in the topic field and press enter.

```
/model/eddiebot/cmd_vel
```

Then run the simulation and try to move the robot using the keyboard. 

# Exercise 3

Create a custom ROS2 package that takes camera sensor data and does the following when faced with an object of a specified color:

- Red: The robot stops. The robot turns left on the spot and then moves straight.
- Yellow: The robot stops. The robot turns right on the spot and then goes straight.
- Green: The robot stops. The robot has reached its destination and is spinning on the spot.

Obtain the amount of rotation of the robot and find the intensity threshold of each color that if passed the robot has to do the corresponding command for that color. (for example, how much red should the image have for the robot to  do the corresponding command). The robot must reach its the destination.

by using

```shell
$ ros2 interface show sensor_msgs/msg/Image
```

Check the image message type and if necessary use [*GitHub search*](https://github.com/search?q=sensor_msgs%2Fmsg%2FImage+rclcpp+language%3AC%2B%2B&type=code&l= C%2B%2B) to check out sample codes that use camera sensor data.

Design a launch file that first calls the launch file of the previous exercise and then starts the necessary bridges for the topics related to the normal image of the Kinect sensor and the speed control of the robot. Finally, it should run the node you created.