|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |



# Exercise 1

Pull the latest changes from the [arashsm79/eddiebot-ros](https://github.com/arashsm79/eddiebot-ros) repository into your ws. Eddie is now controlled using DiffDrive. Check out the [gazebosim documentation](https://gazebosim.org/api/sim/7/annotated.html) and find the page for the VelocityControl plugin (used in the previously to control the eddie) and the new DiffDrive plugin. In one to two paragraphs, write the difference between these two plugins and how they are used.

# Exercise 2

The LIDAR sensor uses light rays to find the distance to objects and can be used, for example, to make a map of the environment. Read [*this page*](https://articulatedrobotics.xyz/mobile-robot-8-lidar/) for a general overview of how this sensor works. The price of these sensors in the market is higher than sensors like Kinect. Therefore, in some applications, the Kinect depth camera can be used instead of the expensive LIDAR sensor. Clone the [depthimage_to_laserscan ](https://github.com/ros-perception/depthimage_to_laserscan) repository into your ws:
```shell
git clone https://github.com/ros-perception/depthimage_to_laserscan.git -b ros2
```
Then install the dependencies with rosdep. This package takes the depth_image data, selects a row from it, and converts it to a LaserScan.

Write a launch file that does all of the following after starting the maze world with Eddie in it (Reminder: see how to add [remapping](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Using-ROS2-Launch-For-Large-Projects.html#remapping) in the launch file):

1. It creates a bridge for the following topics:

     * model/eddiebot/tf/ and then remaps it to tf. 
     * kinect_rgbd_camera/camera_info/
     * kinect_rgbd_camera/depth_image/

2. The depth image to lase scan node. You need to remap the `depth_camera_info` and `depth` topics. Echo the new topic related to scan and see its header contents. What is the name of the frame specified in the header? What does this frame represent and what is its relationship with the points in the message?

3. Run Rviz2 and add the LaserScan section to it and specify the relevant topic. Set the size in LaserScan to 0.1.

4. Using the command as an example
```shell
ros2 run tf2_ros static_transform_publisher "0" "0" "0" "0" "0" "0" "foo" "bar"
```
you can send a zero static conversion from parent frame foo to child frame bar in tf. Do the appropriate conversion for all the following frames until their errors disappear in rviz:

* "eddiebot/base_footprint" → "base_footprint"
* "world" → "eddiebot/odom"
* "camera_link" → "camera_depth_frame"

Now add teleop module in gazebo and move Eddie. Move it close to different walls and make sure they are displayed in rviz by the LaserScan display.

# Exercise 3

using
```shell
ros2 run tf2_tools view_frames
```
Explain the different parts of the tf tree.

Notes:
- Please do not use ExecuteProcess or similar functions in the launch file as much as possible and write the description of different parts such as the execution of Nodes correctly.
- If you would like to see the wheels move in rviz, set the `use_sim_time` parameter to true for gazebo and all static bridges and transformations you make.

```shell
$ ros2 launch eddiebot_gazebo eddiebot_gz_sim.launch.py world:='maze' use_sim_time:='true'

$ ros2 run ... --ros-args -p use_sim_time:='true'
```

- In the depthimage_to_laserscan repository, make sure to set the branch to ros2 and then read its README.
