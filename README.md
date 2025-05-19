# -UE22EC342BC2-Sravanthi_Yuktikumar_Differential-Robot-With-a-Custom-Path-Following-Capability

A ROS2 package implementing a differential drive robot with an interactive path following capability using Pygame.
Features

Differential Drive Robot Model: Simple but effective robot design with two wheels
Interactive Path Drawing: Draw paths with mouse and watch the robot follow them
ROS2 Integration: Commands are sent through standard ROS2 topics
Gazebo Simulation: Full 3D simulation environment
Visualization: Real-time visualization using Pygame interface


Prerequisites

ROS2 (Tested with Humble/Iron)
Gazebo
Python 3.8 or newer
pygame

Installation
1. Create a ROS2 workspace:
bashmkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
2. Clone this repository:
bashgit clone https://github.com/your-username/ros2_dd_robot.git
3. Install dependencies:
bashcd ~/ros2_ws
rosdep install --from-paths src --ignore-src -r -y
4. Build the package:
bashcolcon build --packages-select dd_robot
source install/setup.bash
Usage
1. Launch the robot in Gazebo:
bashros2 launch dd_robot gazebo.launch.py
2. Start the path follower interface:
bashros2 run dd_robot path_follower
3. View the robot in RViz (optional):
bashros2 launch dd_robot display.launch.py
User Interface Controls

Left-click and drag: Draw a path
Release mouse button: Start robot following the path
R key: Reset the path
ESC key: Exit the application

Project Structure
dd_robot/
├── dd_robot/               # Python package
│   ├── __init__.py
│   └── path_follower.py    # Main path following implementation
├── launch/                 # Launch files
│   ├── display.launch.py   # Visualization launch
│   └── gazebo.launch.py    # Simulation launch
├── urdf/                   # Robot model files
│   └── ddrobot.urdf        # Robot description file
├── worlds/                 # Simulation world files
│   └── ddrobot.world       # Simple world with an obstacle
├── resource/               # Resource files
│   └── dd_robot            # Package marker
├── package.xml             # Package manifest
└── setup.py                # Package setup file
How It Works
Path Following Algorithm
The robot follows paths using these steps:

The user draws a path in the Pygame window
The path is stored as a series of (x, y) coordinates
The robot calculates the direction to the next point
The system converts direction into linear and angular velocities
Velocity commands are published to the /cmd_vel topic
The robot moves to follow the path point by point

ROS2 Integration
The system integrates with ROS2 through:

Publishing to the standard /cmd_vel topic
Using standard geometry_msgs/Twist messages
Running the ROS2 node in a separate thread

Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

Fork the project
Create your feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add some amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request

License
This project is licensed under the MIT License - see the LICENSE file for details.
Acknowledgements

ROS2 development team for the excellent robotics framework
Pygame community for the interactive graphics library
Gazebo team for the 3D simulation capabilities


