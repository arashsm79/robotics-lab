|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

## Learning Basic Concepts
Read the following guides and documentation and do the tasks in each tutorial step by step.
*  [Understanding nodes](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)
*  [Understanding topics](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html)
*  [Understanding services](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Services/Understanding-ROS2-Services.html)
*  [Understanding parameters](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Parameters/Understanding-ROS2-Parameters.html)
*  [Understanding actions](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Actions/Understanding-ROS2-Actions.html)
*  [Using `rqt_console` to view logs](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Using-Rqt-Console/Using-Rqt-Console.html)
*  [Launching nodes](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Launching-Multiple-Nodes/Launching-Multiple-Nodes.html)
*  [Recording and playing back data](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html)

## Exercise 1

a) We know that each executable file can have several nodes. If we want to change the turtle1 node name to my_turtle01 in the turtlesim package and turtlesim_nodes executable file, what command can we use? [[Remapping](https://design.ros2.org/articles/ros_command_line_arguments.html#name-remapping-rules)] (note that there are several nodes with different names in the executable program)
b) We want to send a `geometry_msgs/msg/Pose` message to the `/robot/pose` topic through the CLI with an interval of 2 messages per second. Write the required command.  [[geometry_msgs](https://docs.ros2.org/latest/api/geometry_msgs/index-msg.html)], [[Quaternion](https://docs.ros.org/en/humble/Tutorials/Intermediate/Tf2/Quaternion-Fundamentals.html)]
c) First, get information about `turtlesim/srv/SetPen` type with the `ros2 interface show` command and write a command that sends a request to the `turtle1/set_pen` service. 
d) Is it possible to simulate the behavior of an action with a set of topics and services? Explain.
e) What is the default log level in ROS? Why was this decision made?
f) Draw the last digit of your student number in turtlesim using teleop and record it using bag. You will be prompted to play it again in person.

## Programming in ROS

1)  [Using **colcon** to build packages](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html)
2)   [Creating a workspace](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html)
3)   [Creating a package](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html)
4)   [Writing a simple publisher and subscriber (C++)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Cpp-Publisher-And-Subscriber.html)
5)   [Writing a simple publisher and subscriber (Python)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html)
If you are using distrobox, this [link](https://github.com/89luca89/distrobox/blob/main/docs/posts/integrate_vscode_distrobox.md) can help you develop software inside it using VSCode.

## Exercise 2
Bob wants to send a message to Alice through a topic. For this, he encrypts his message using the key they shared before, as XOR Encryption, and sends it character by character in the thread. Bob also puts a delimiter at the end of his message to indicate the end of the message. Bob and Alice both know what this delimiter is. Bob does this intermittently; In this way, the first digit of the key is XORed with the first character of the message and sent in the topic, and if it reaches the end of the message, it starts again from the beginning. Both message and key length is 10.
Design two packages named bobsim and alicesim that contain bobnode and alicenode respectively. Implement bobsim using C++ and alicesim using Python. The common key between the two nodes is your student number and the string that bobnode sends character by character periodically.
SEND_HELP!
Is. Choosing the topic name, topic message type, and message separator is optional. After the alicenode receives the message and decodes it, it prints it and exits.
Print the topic messages in a terminal using echo and take a screenshot along with the alicenode output at the end of the execution.
