# Robot Arm Control

This repository contains all the necessary files and instructions to control a robot arm using ROS Noetic, joint_state_publisher, and MoveIt.

## Prerequisites

- ROS Noetic
- Catkin
- MoveIt

## Setup

### 1. Install ROS Noetic
Follow the instructions from [ROS Noetic Installation](http://wiki.ros.org/noetic/Installation/Ubuntu).

### 2. Create a catkin workspace
```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 3. Clone the robot arm package
```bash
cd ~/catkin_ws/src
sudo apt install git
git clone https://github.com/smart-methods/arduino_robot_arm
```

### 4. Install dependencies
```bash
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
sudo apt-get install ros-noetic-moveit
sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```

### 5. Build the workspace
```bash
cd ~/catkin_ws
catkin_make
```


![Screenshot (52)](https://github.com/user-attachments/assets/c625658d-6a81-4fbd-8829-1cb5d736c62f)


![Screenshot (53)](https://github.com/user-attachments/assets/d53735ec-e575-42bf-941d-1265a46a502f)


![Screenshot (54)](https://github.com/user-attachments/assets/fb1be1b5-fcde-4065-b595-598a6994fcc1)





## Usage

### 1. Running the Motor Control Node
```bash
roslaunch robot_arm_pkg check_motors.launch
```

### 2. Controlling Motors using joint_state_publisher
```bash
roslaunch robot_arm_pkg check_motors_gazebo.launch
```
Ensure the script has execution permissions:
```bash
cd ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts
sudo chmod +x joint_states_to_gazebo.py
```

![Screenshot (55)](https://github.com/user-attachments/assets/3baefb39-d4db-46e6-9e5c-079f6a0ca945)


![Screenshot (56)](https://github.com/user-attachments/assets/c7d7acc6-05a1-4024-8523-9da21f16cf68)


![Screenshot (57)](https://github.com/user-attachments/assets/1e912bae-8ed4-4756-9469-032f8c928e56)



### 3. MoveIt Setup and Execution
Install MoveIt:
```bash
sudo apt-get install ros-noetic-moveit
```
Create a MoveIt config package:
```bash
roslaunch moveit_setup_assistant setup_assistant.launch
```
Follow the instructions in the MoveIt Setup Assistant to create a configuration package for the robot arm.

Run MoveIt:
```bash
roslaunch moveit_pkg demo.launch
```
Run MoveIt with Gazebo:
```bash
roslaunch moveit_pkg demo_gazebo.launch
```

![Screenshot (60)](https://github.com/user-attachments/assets/085cca54-7dc3-42c2-bfd7-eb94fa2a36f1)


![Screenshot (61)](https://github.com/user-attachments/assets/052cc761-02b5-4147-93ec-cd6f60af09d8)


![Screenshot (62)](https://github.com/user-attachments/assets/d4a9acca-d4b8-4f5e-9a53-39df256f7807)


![Screenshot (63)](https://github.com/user-attachments/assets/c1a2c95e-84f1-4a64-97d6-3ab79237348c)





## Troubleshooting

- **Failed to find launch file**:
  Ensure that the launch file exists in the correct directory. Check the path and file name for typos.
  ```bash
  cd ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/launch
  ls
  ```

- **Permission denied for scripts**:
  Make sure the scripts have the necessary execution permissions.
  ```bash
  sudo chmod +x ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts/*.py
  ```

- **Source the setup.bash**:
  After building the workspace, always source the setup.bash file.
  ```bash
  source ~/catkin_ws/devel/setup.bash
  ```


## Acknowledgements

This project is based on the work by [smart-methods](https://github.com/smart-methods).

[GitHub Repository](https://github.com/smart-methods/arduino_robot_arm)
