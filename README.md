# Turtlebot Maze Navigation Project

## Overview
This project involves developing a Turtlebot capable of autonomously traversing a maze in a simulated environment using ROS (Robot Operating System). The key objectives are:
- Implementing an Extended Kalman Filter (EKF) for real-time state estimation of the Turtlebot.
- Navigating and solving the maze using the left-hand rule.
- Successfully docking at a target location marked by a reflective panel.

## Features
- **Extended Kalman Filter (EKF):** Provides real-time position estimation using odometry and sensor data, published on the `/estimate` topic.
- **Left-Hand Rule Navigation:** A classic algorithm for maze solving, allowing the Turtlebot to follow the left-hand wall to reach the maze exit.
- **Reflective Panel Detection:** Identifies and navigates towards a reflective panel in the environment, utilizing Lidar data.

## Project Structure

### 1. Kalman Filter Implementation
The EKF is designed to estimate the Turtlebot's position and orientation by fusing odometry and sensor data. It includes:
- **State Variables:** Position `(x, y)`, orientation `θ`, longitudinal velocity `vl`, and angular velocity `vω`.
- **Estimation:** The state evolution equations predict the next state based on the current state and velocity.
- **Correction:** The filter corrects its estimates using odometry data, ensuring accurate tracking of the robot's pose.

### 2. Maze Navigation
The Turtlebot navigates the maze using the left-hand rule:
- **Sensors:** A Lidar sensor provides distance measurements from surrounding walls.
- **Zones:** The Lidar scan is divided into four zones (front, right, back, left) to detect obstacles.
- **Navigation Strategy:** Based on the presence of walls in these zones, the Turtlebot decides whether to move forward, turn left, or turn right.

### 3. Reflective Panel Docking
The final task is docking at a reflective panel:
- **Detection:** The Turtlebot uses Lidar to detect the panel by analyzing the intensity of reflected light.
- **Docking:** Once the panel is detected, the robot aligns itself with the panel and moves towards it, adjusting its position as needed.

## Simulation
The project is simulated in the Gazebo environment:
- **Gazebo:** Provides a realistic 3D environment for testing the Turtlebot's navigation and docking capabilities.
- **ROS:** Manages communication between the Turtlebot's components, including sensor data processing, control commands, and EKF updates.

## Installation

### Prerequisites
- **ROS Noetic**
- **Gazebo**
- **Turtlebot3 Packages**

### Setup
1. Clone this repository:
    ```bash
    git clone https://github.com/yourusername/turtlebot_maze_navigation.git
    cd turtlebot_maze_navigation
    ```
2. Install the required dependencies:
    ```bash
    sudo apt-get install ros-noetic-turtlebot3 ros-noetic-turtlebot3-simulations
    ```
3. Build the project:
    ```bash
    catkin_make
    ```
4. Source your workspace:
    ```bash
    source devel/setup.bash
    ```

### Running the Simulation
1. Launch the Gazebo simulation:
    ```bash
    roslaunch turtlebot_maze_navigation maze_world.launch
    ```
2. Start the Turtlebot navigation node:
    ```bash
    roslaunch turtlebot_maze_navigation navigation.launch
    ```

## Results
- The Turtlebot successfully navigates through the maze using the left-hand rule.
- EKF provides accurate real-time pose estimation.
- The Turtlebot detects and docks at the reflective panel efficiently.

## Limitations
- The EKF accuracy is dependent on the quality of the odometry data.
- Maze complexity and reflective panel placement may affect docking precision.

## Future Work
- Improving EKF by incorporating additional sensors (e.g., IMU).
- Enhancing the maze-solving strategy for more complex mazes.
- Implementing advanced docking techniques for dynamic environments.

## Authors
- Rémi Bordes
- Victor Demessance

## Acknowledgements
Special thanks to [University Name] for providing the resources and support for this project.

