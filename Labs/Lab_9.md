|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

In this experiment, we are going to add odometry to the mobile robot designed in the previous experiment so that the robot can approximate its current location based on the rotation rate and speed of its wheels. Odometry is about using data from sensors to estimate the change in position, orientation, and velocity of a robot over time relative to a point (for example, a frame centered on this point could be *odom* which could be placed at x=0, y=0 z=0). Odometry information is usually obtained from sensors such as wheel encoder and IMU. Finally, the conversion between the robot frame and the odom frame must be sent in tf to approximate the location of the robot in the world.

In ROS, the coordinate frame used for odometry is known as the `odom` frame. The `odom` frame is the point in the world where the robot first starts to move. The position and orientation of a robot in the `odom` frame becomes less accurate over time and distance because sensors such as IMUs (which measure acceleration) and wheel encoders (which measure the number of times each wheel rotates) are not error-free. For example, imagine your robot hits a wall. Its wheels may spin repeatedly without the robot moving anywhere (we call this wheel slip). In this case, the wheel odometry thinks that the robot has traveled a distance, while it is standing still; We must manage these inaccuracies.

Therefore, the way frames are connected is as follows:

1. map =\> odom
2. odom =\> chassis
3. chassis =\> base_laser (sensor base frames)

The first transform is usually sent by the localization and mapping system (in this experiment we give manual and static transform). The second transformation is sent by the odometry system such as IMU. The third transformation is sent by robot_state_publisher and the robot's URDF file.

# Exercise 1

This exercise is also done in the maze world. First, add another caster wheel to the end of the robot to make the robot more stable. Then find the page for [differential drive plugin](gazebosim.org/api/sim/7/annotated.html) (set the detail level to 5 so you can search more easily). Add the necessary tags to the plugin to send odometry info to the `/odom` topic instead of the default topic. Echo the topic and take a screenshot of the terminal output with the robot. Between which two frames is Odometry being sent?

# Exercise 2

Create a bridge for the LaserScan topic in the previous exercise. Create another bridge that connects the tf topic of the robot in gazebo to ros2. (Reminder on how to add [remapping](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Using-ROS2-Launch-For-Large-Projects.html#remapping) in a launch file)

Use the following command to find out about the topic message type in Gazebo.

```shell
gz topic -i -t topic_name
```

Using the `static_transform_publisher` that we used in the previous exercise, create two static transform nodes:

1. Connect the `gpu_lidar` to `chassis.
2. Connect `odom` to `world`.

  Write a launch file that does all the work for this exercise.

# Exercise 3

In rviz2, first add a LaserScan display and increase the Grid size. Specify required topics and make sure tf has no warnings. Set the size value in LaserScan to 0.1.

Now move the robot using teleop, you should be able to see the robot frame movement in rviz2 and the LIDAR sensor values will be on the correct side of the world depending on the direction of the robot.