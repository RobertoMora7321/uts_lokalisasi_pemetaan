# TurtleBot4 Setup & Run Guide

This guide explains how to set up your workspace, build the project, and run TurtleBot4 with navigation, localization, RViz visualization, and custom packages.

## 1. Create Workspace & Build

### 1.1 Create a workspace
```bash
mkdir -p ~/turtlebot4_delivery/src
cd ~/turtlebot4_delivery/src
```

### 1.2 Clone the GitHub repository
```bash
git clone https://github.com/MarcellinoAcel/pose_nav_turtle.git
```

### 1.3 Build using colcon
```bash
cd ~/turtlebot4_delivery
colcon build
```

### 1.4 Source the workspace
```bash
source install/setup.bash
```

## 2. Visualization (RViz)

### Option A: Run RViz remotely via SSH
```bash
ssh -X ubuntu@192.168.185.3
ros2 launch turtlebot4_viz view_navigation.launch.py
```

### Option B: Run RViz locally
```bash
ros2 launch turtlebot4_viz view_robot.launch.py
```

## 3. Localization

**(New terminal)** Connect to robot:
```bash
ssh ubuntu@192.168.185.3
cd ~/turtlebot4_delivery
source install/setup.bash
ros2 launch pose_nav_turtle localization.launch.py map:=src/pose_nav_turtle/maps/map_uts_kel1.yaml
```

**In RViz:**
- Use **2D Pose Estimate** to set initial pose

## 4. Run Navigation Package

**(New terminal)** Connect and launch:
```bash
ssh ubuntu@192.168.185.3
cd ~/turtlebot4_delivery  
source install/setup.bash
ros2 launch pose_nav_turtle run_nav.launch.py
```

## 5. Run Additional Nodes

**(New terminal)** Run custom node:
```bash
ssh ubuntu@192.168.185.3
cd ~/turtlebot4_delivery
source install/setup.bash
ros2 run pose_nav_turtle pose_nav_turtle
```

## 🚀 You're Ready!

**Happy robot testing!** 🤖
