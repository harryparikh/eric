# ROS2 Navigation Assignment – Parikh Harry Satyen

## Overview
This project implements a modular ROS2 Navigation2 (Nav2) setup for the ERIC Robotics Testbed-T1.0.0 robot.

Instead of directly using `nav2_bringup`, the navigation stack was manually configured using:
- `map_server`
- `amcl`
- planner plugins
- controller plugins
- behavior tree navigator

The objective was to create a modular navigation workflow with separate launch files for:
- map loading
- localization
- navigation

The project was developed and tested on ROS2 Humble with Gazebo and RViz.

---

# Workspace Structure

```bash
assignment_ws/
├── README.md
├── frames_2026-05-26_17.35.13.gv
├── frames_2026-05-26_17.35.13.pdf
└── src
    ├── l1-harryparikh
    │   ├── help.md
    │   ├── README.md
    │   ├── testbed_bringup
    │   ├── testbed_description
    │   └── testbed_gazebo
    └── testbed_navigation
        ├── config
        │   ├── amcl_params.yaml
        │   └── nav2_params.yaml
        ├── launch
        │   ├── localization.launch.py
        │   ├── map_loader.launch.py
        │   └── navigation.launch.py
        ├── include
        ├── src
        ├── CMakeLists.txt
        └── package.xml
```

---

# Features Implemented

## 1. Manual Map Loading
Implemented map loading using:
- `nav2_map_server`

Launch File:
```bash
map_loader.launch.py
```

Map Used:
```bash
testbed_world.yaml
```

---

## 2. Localization using AMCL
Implemented robot localization using:
- `nav2_amcl`

Configured:
- AMCL parameters
- initial pose handling
- map-to-odom transform

Files:
```bash
config/amcl_params.yaml
launch/localization.launch.py
```

---

## 3. Navigation Stack
Implemented modular Nav2 navigation using:
- Planner Server
- Controller Server
- BT Navigator
- Recoveries Server

Configured in:
```bash
config/nav2_params.yaml
```

Launch File:
```bash
launch/navigation.launch.py
```

---

# Packages Used

## Existing Packages
- `testbed_description`
- `testbed_bringup`
- `testbed_gazebo`

## Developed Package
- `testbed_navigation`

---

# Build Instructions

## 1. Create Workspace
```bash
mkdir -p ~/assignment_ws/src
```

## 2. Clone Repository
```bash
cd ~/assignment_ws/src
git clone <repository-url>
```

## 3. Build Workspace
```bash
cd ~/assignment_ws
colcon build
source install/setup.bash
```

---

# Running the Project

## 1. Launch Simulation
```bash
ros2 launch testbed_bringup testbed_full_bringup.launch.py
```

---

## 2. Load Map
```bash
ros2 launch testbed_navigation map_loader.launch.py
```

---

## 3. Start Localization
```bash
ros2 launch testbed_navigation localization.launch.py
```

---

## 4. Start Navigation
```bash
ros2 launch testbed_navigation navigation.launch.py
```

---

# Testing
The navigation stack was tested in Gazebo and RViz by:
- setting initial pose
- sending 2D Nav Goals
- verifying localization accuracy
- verifying robot path planning and movement

---

# Author

## Contact Info 
 - Name: Parikh Harry Satyen
 - Contact number: +91 9426346371
 - Email Address: harry.s.parikh@gmail.com
