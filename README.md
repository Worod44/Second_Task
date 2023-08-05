# Second_Task

### Use Turtlebot3 with SLAM approach to create and save a map
##### After we have downloaded Ubuntu and installed the Ros system on it, we will use Turtlebot3 with the SLAM approach to create and save the robot path map


#### 1-The first step is to download Ros on our PC
```
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh
```

#### 2-Install Dependent ROS Packages
```
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
```

#### 3-Install TurtleBot3 Packages
```
$ sudo apt install ros-noetic-dynamixel-sdk
$ sudo apt install ros-noetic-turtlebot3-msgs
$ sudo apt install ros-noetic-turtlebot3
```

#### 4-Building TurtleBot3 package from source
```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/DynamixelSDK.git
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
$ cd ~/catkin_ws && catkin_make
$ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

#### 5- Now operate gazebo and teleop TurtleBot3
###### Run gazebo
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
<img width="500" alt="T21" src="https://github.com/Worod44/Second_Task/assets/95488818/22bd7f07-ea17-4deb-b80e-26d23a6c5c2e">

###### Run Teleoperation Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
<img width="500" alt="T22" src="https://github.com/Worod44/Second_Task/assets/95488818/f6039428-8c4f-4b47-81c8-dadc99ecca0b">

#### 6- Slam and save the map
###### Run Rviz and Draw the map
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```


<img width="280" alt="T23" src="https://github.com/Worod44/Second_Task/assets/95488818/ec95ec3b-9c90-4bbb-b733-166bc1166764">
<img width="300" alt="T24" src="https://github.com/Worod44/Second_Task/assets/95488818/18bc32e9-c71f-4922-bfcb-127381e73249">
<img width="270" alt="T25" src="https://github.com/Worod44/Second_Task/assets/95488818/deadd2c1-8717-443d-b94b-35117e1503fb">


###### Save Map
```
$ rosrun map_server map_saver -f ~/map
```
<img width="400" alt="T26" src="https://github.com/Worod44/Second_Task/assets/95488818/47943a31-55f6-4d86-97c1-8d9e97655339">



