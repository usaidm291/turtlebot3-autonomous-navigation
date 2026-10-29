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
Usaid Ahmed Mansabdar

## Demo Video

The autonomous navigation demonstration is available at:
`results/demo.mp4`

The recording shows the TurtleBot3 navigating to a goal selected in
RViz2 while its movement is simulated in Gazebo.

## Challenges and Learnings

- Setting up the ROS 2 Humble simulation and Nav2 navigation stack.
- Understanding the relationship between Gazebo, RViz2, TF frames,
  odometry, laser scans, and AMCL localization.
- Sending navigation goals through RViz2 and observing autonomous
  path planning and movement.

## Reproducing the Demonstration

Use the launch commands above in separate terminals. Wait for the
simulation and navigation stack to initialize before sending a goal
through RViz2.

The project uses the installed TurtleBot3 world and navigation map.
It does not currently include a custom-built map or a custom Nav2
planner.

## Included Configuration and Map

- `config/burger.yaml`: TurtleBot3 Burger Nav2 parameters copied from
  the installed ROS 2 Humble TurtleBot3 navigation package.
- `maps/map.yaml` and `maps/map.pgm`: The map used for the simulation.
- `results/demo.mp4`: Autonomous navigation demonstration.

## Run Using the Repository Files

Clone the repository and enter its directory:

    git clone https://github.com/usaidm291/turtlebot3-autonomous-navigation.git
    cd turtlebot3-autonomous-navigation

Start Gazebo in one terminal:

    source /opt/ros/humble/setup.bash
    export TURTLEBOT3_MODEL=burger
    ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

Start Nav2 in a second terminal from the project directory:

    source /opt/ros/humble/setup.bash
    export TURTLEBOT3_MODEL=burger
    ros2 launch turtlebot3_navigation2 navigation2.launch.py map:=$(pwd)/maps/map.yaml params_file:=$(pwd)/config/burger.yaml use_sim_time:=True

Wait for navigation to initialize. In RViz2, use Nav2 Goal to select
a destination and observe autonomous movement.

Note: ROS 2 Humble, TurtleBot3 packages, Gazebo Classic, and RViz2
must be installed before running the project.
