
|  Introduction to Robotics |  Ferdowsi University of Mashhad |
|---|---|
|  Instructor: Arash Sal Moslehian |  Computer Engineering Dept. |

# Getting to know the basic concepts

Read the instructions below and proceed step by step.

-   [Managing Dependencies with rosdep](https://docs.ros.org/en/humble/Tutorials/Intermediate/Rosdep.html)
-   [Using](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Getting-Started-With-Ros2doctor.html)[**ros2doctor**](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Getting-Started-With-Ros2doctor.html)[to identify issues](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Getting-Started-With-Ros2doctor.html)
-   [Writing a simple service and client (C++)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Cpp-Service-And-Client.html)
-   [Writing a simple service and client (Python)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Service-And-Client.html) -   [Creating custom msg and srv files](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Custom-ROS2-Interfaces.html)
-   [Implementing custom interfaces](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Single-Package-Define-And-Use-Interface.html)
-   [Using parameters in a class (C++)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Using-Parameters-In-A-Class-CPP.html)
-   [Using parameters in a class (Python)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Using-Parameters-In-A-Class-Python.html)
-   [Creating an action](https://docs.ros.org/en/humble/Tutorials/Intermediate/Creating-an-Action.html)
-   [Writing an action server and client (C++)](https://docs.ros.org/en/humble/Tutorials/Intermediate/Writing-an-Action-Server-Client/Cpp.html)
-   [Writing an action server and client (Python)](https://docs.ros.org/en/humble/Tutorials/Intermediate/Writing-an-Action-Server-Client/Py.html)

After reading *all* of the above, do the exercises.

# Exercise 1

1) What is the difference between the packages in [rosdistro/rosdep/base.yaml](https://github.com/ros/rosdistro/blob/master/rosdep/base.yaml) and those that are located in [rosdistro/humble/distribution.yaml](https://github.com/ros/rosdistro/blob/master/humble/distribution.yaml)?
2) According to the previous question, in what category does the `slam_toolbox` package fall and How will rosdep install it? How about the `ffmpeg` package?
3) Briefly explain in one paragraph what IDL is and How ROS uses it. [IDL Spec](https://www.omg.org/spec/IDL/), [ROS IDL Mapping](https://design.ros2.org/articles/idl_interface_definition.html), [rosidl](https://docs.ros.org/en/rolling/Concepts/About-Internal-Interfaces.html#the-rosidl-repository)

# Exercise 2

Yin and Yang want to talk to each other. Create two packages yinsim (Python) and yangsim (C++) which contain yinnode and yangnode respectively.

## Services
Each node has a service. To send a message, in one step, yin sends its message in the role of a client, and in the next step, yang does the same thing. The message sent from the client side to the service contains a string and the length of the string, and the service sends the numerical sum of the characters of the received string in response. (The characters are all ASCII) Each node, upon receiving the other party's message, sends it in the `/conversation` topic using the following format:

```
<name> said: <msg>, <length>, <checksum>
```

Sends where \<name\> is the name of the opposite node, \<msg\> is the message received from the opposite node, \<length\> is the length of the message and \<checksum\> is the numerical sum of the characters of the received string. The whole message is of string type.

## Parameters

- shout: each node takes a parameter named shout, if its value is true, the node will put its messages in a \*\* pair. The default value of this parameter is false. For example:
     \*\*Aaahhhh\*\*
- opacity: the yin node takes a parameter named opacity, which is set to 100 by default.

## Action

The yin node has an action server that takes a string request. If this string contains the word `bye`, it will set its opacity variable to 0 from whatever value it has and sends the current value in feedback. When the opacity reaches 0, it sends the string `farewell` in the result and exits.

Create your own messages in a separate package called yinyang_msgs for the messages used in the service and action.
Note that depending on your implementation, you can add other items to the message type. For example, the client's request can include other things besides string and string length.
Both nodes know the name of the opposite node. The number of sentences for each node is seven sentences. At the end of the conversation, Yang, in the role of action client, sends a string with the value `Good bye` to the action server that Yin has, and prints the feedback and result and exits.

**Dialogue text \[1\] for Yin:**
\"I am Yin, some mistake me for an actual material entity but I am more
of a concept",

\"Interesting Yang, so one could say, in a philosophical sense, we are
"two polar elements",

\"We, Yang, are therefore the balancing powers in the universe.\"

\"Difficult and easy complete each other.\"

\"Long and short show each other.\"

\"Noise and sound harmonize each other.\"

"You shine your light."

**Dialogue text \[1\] for Yang:**

\"Hi Yin, I am Yang the opposite of you.\"

\"Yes, Yin; we ourselves, do not mean anything since we are alone
employed to express a relationship",

\"Precisely, Yin; we are used to describe how things function in
relation to each other and to the universe.

\"For what is and what is not beget each other.\"

\"High and low place each other.\"

\"Before and behind follow each other.",

"And you fade into the darkness."

Echo the `/conversation` topic in a terminal and run the two nodes. Take a screenshot of the output of all terminals.

\[1\] *Tao Te Ching, Book by Laoz*
