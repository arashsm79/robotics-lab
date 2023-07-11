
|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

Read the instructions below and proceed step by step.

- [Creating a launch file](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Creating-Launch-Files.html)
- [Launching and monitoring multiple nodes](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Launch-system.html)
- [Learning TF2](https://docs.ros.org/en/humble/Tutorials/Intermediate/Tf2/Tf2-Main.html#learning-tf2) (using your preferred language)
- [URDF](https://docs.ros.org/en/humble/Tutorials/Intermediate/URDF/URDF-Main.html)
- [Simulating a Robot with Gazebo](https://docs.ros.org/en/humble/Tutorials/Advanced/Simulators/Gazebo.html)

# Exercise 1

* Write a launch file in YAML format for bob and alice nodes in assignment 1.
* For the yin and yang nodes in assignment 2, write a launch file in YAML format in which the `shout` and `opacity` parameters are set to arbitrary values. 
* How does TF2 prevent loop formation in its transformations?
* What is the use of `static_transform_publisher`?
* What is the difference between dynamic and static transformations and where are they used?
* How are TF2 and URDF trees related?

# Exercise 2

Design a package called `turtlemania` that creates 3 turtles in addition to the original turtle. The first turtle must follow the initial turtle with a delay of 2 seconds. The second turtle must follow the first turtle with a delay of 2 seconds, and the third turtle must follow the second turtle with a delay of 2 seconds. For example, in the case of the second turtle, 2 seconds delay means what the position of the first turtle 2 seconds ago compared to the current position of the second turtle is.

Move the initial turtle using teleop. Use a launch file to run your system. You can use the codes for [turtle_tf2 demo](https://github.com/ros/geometry_tutorials/blob/ros2/turtle_tf2_py) that was used in the tutorials.