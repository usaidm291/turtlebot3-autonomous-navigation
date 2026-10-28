# TurtleBot3 Autonomous Navigation using ROS 2 Nav2

## Overview
This project demonstrates autonomous navigation of a TurtleBot3 Burger
in Gazebo using ROS 2 Humble, RViz2, and Navigation2 (Nav2).

The robot receives a goal through RViz2 and travels to it autonomously.

## Requirements
- Ubuntu 22.04
- ROS 2 Humble
- TurtleBot3 Burger
- Gazebo Classic
- RViz2
- Navigation2

## How to Run

### Terminal 1: Start Gazebo
Open a terminal and run:

    source /opt/ros/humble/setup.bash
    export TURTLEBOT3_MODEL=burger
    ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

### Terminal 2: Start Navigation2
Open another terminal after Gazebo starts and run:

    source /opt/ros/humble/setup.bash
    export TURTLEBOT3_MODEL=burger
    ros2 launch turtlebot3_navigation2 navigation2.launch.py map:=/opt/ros/humble/share/turtlebot3_navigation2/map/map.yaml params_file:=/opt/ros/humble/share/turtlebot3_navigation2/param/humble/burger.yaml use_sim_time:=True

### Navigation
In RViz2, set Fixed Frame to map. Use Nav2 Goal to select a destination
and observe the robot travel to it without manual movement control.

## Project Structure
- src/: Source files
- config/: Configuration files
- maps/: Map files
- results/: Demo evidence

## Tested Result
The robot successfully travelled to a selected Nav2 goal in the Gazebo
simulation while its movement was visualized in RViz2.

## Author
TurtleBot3 Autonomous Navigation Project
