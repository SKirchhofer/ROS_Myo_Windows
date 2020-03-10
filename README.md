# ROS_Myo_Windows
ROS package for the Myo armband on Windows

## General informations

It is based on the Myo SDK 0.9.0 for Windows. Tested on windows 10 x64 with ROS Melodic and Myo Connect 1.0.1.

The ROS message associated to the Myo contains a vector with electromyographic signals (6 channels).


## How to use it

Download and install the Myo Connect software for Windows 1.0.1. https://support.getmyo.com/hc/en-us/articles/360018409792-Myo-Connect-SDK-and-firmware-downloads

The CMakeList file and the system path might be modified to match your configuration :
- Line 153 of the CMakeList file : The root to the the myo64.lib file must be specified. For exemple, if the package is in the workspace "C:\catkin_ws\", the root to the myo64.lib is "C:\catkin_ws\src\ros_myo\lib\myo64.lib". Use "myo64.lib" for a 64 bits system or "myo32.lib" for a 32 bits system.
- The root of the dll file must be added to the system path (ros_myo/lib). For this exemple, add "C:\catkin_ws\src\ros_myo\lib".

Once the package is build, you can run the myo node with :
```
rosrun ros_myo ros_myo_node
```
The node **ros_myo_node** sends **EmgArray** messages on the **myo_raw** topic.
The content of the message can be found in the folder "ros_myo/msg".

If you want to get more informations from the myo, you might want to modify the file "ros_myo/src/sender.cpp". 
