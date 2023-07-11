|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

## Build Tools

Please read the following instructions carefully and follow them step by step.

- [Using](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)[colcon ](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)[to build packages](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)

To prevent RAM from suddenly filling up, give colcon the following settings.

```
--parallel-workers 1
```

# Exercise 1

Run the demo mentioned in the tutorial and let it run until the displayed number reaches the last digit of your student number + 5. 

# Exercise 2

Clone the following package in src and build it with colcon.

```
$ git clone https://github.com/kalashjain23/turtlechaser.git
```

If needed, type the following two commands in your workspace folder first.

```
$ rosdep update

$ rosdep install -i --from-path src --rosdistro humble -y
```

You can use the following commands to build and run the project: (Depending on your environment, it may need changes)

```shell
$ colcon build --symlink-install --parallel-workers 2
--packages-select turtlechaser

$ source ~/turtlechaser_ws/install/local_setup.bash

$ ros2 launch turtlechaser turtlechaser.launch.py
```

Wait until the number of turtles is equal to the last digit of your student number + 5.