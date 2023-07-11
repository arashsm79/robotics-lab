|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

The purpose of this exercise is to install and run ROS. Robot Operating System (ROS) is a collection of libraries and software tools for building robot programs. From advanced drivers and algorithms to powerful developer tools, ROS has free and open source tools used for robotics projects around the world.
ROS1 started in 2007. In 2017, the first version of ROS2 was released, which solved many problems that developers had with ROS1. Since active development of ROS1 is virtually complete, this course will focus on ROS2 and the Humble Hawksbill release so that the lessons learned will remain relevant to the industry well into the future. From now on, by ROS I mean ROS2.
ROS has a very good and complete documentation which can be viewed at [this link](https://docs.ros.org/en/humble/index.html). During the semester,  students are to read the specified parts and do the their exercises.

## Installation
Please use [this link](https://docs.ros.org/en/humble/Installation.html) for different methods of installing ROS in various operating systems. If you have problems installing ROS on your platform, search for solutions using the internet and search engines. Below is the suggested method for installation. This method is container-based and has minimal impact on the base system so that by deleting the container, no traces of ROS remain on the system. Due to the many dependencies and the complexity of communication between ROS packages, it is strongly recommended that you avoid installing it normally on your main system.
The following description is for Linux only. It is recommended to use Linux for all development work.

First, install [distrobox](https://github.com/89luca89/distrobox) and read its description. Then, with the following command, create a container in which ROS is already installed.
```shell
$ distrobox create --image osrf/ros:humble-desktop-full-jammy --name rosbox
```
Then with
```shell
$ distrobox enter rosbox -- bash
```
Enter the container. ROS must be available on the following path:
```
/opt/ros/...
```
You can proceed with the installation documentation from here on.
If you encounter access problems in opening graphical applications, the following command may solve it.
```shell
$ xhost +SI:localuser:$USER
```

## Working with CLI tools
Read the following two pages and take the necessary steps to ensure the correct installation of ROS.
* [Configuring environment](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html)
* [Using turtlesim and rqt](Using turtlesim and rqt)

If you used the container method, rqt and turtlesim are already installed and you can skip the installation part of the tutorial.

## Exercise
Using rqt and `turtle_teleop_key`, create two turtles with different color trails and draw your initials on the screen. (If the first letters of your name and last name are more than two letters, draw only the first two letters). For example, if a person's name is John Doe. It can have a red turtle that draws J and a blue turtle that draws D. The letters do not have to be perfect, and letters with smooth and broken lines are also acceptable. You can use tmux for convenience.