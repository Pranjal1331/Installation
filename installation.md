# Installation
Instructions to run and install the F1Tenth Simulator.

The following set of instructions are to be used only for Ubuntu 20.04 and above.
The current F1Tenth Simulator is designed to work on ROS Foxy which is native to Ubuntu 20.04.

These instructions will need to be updated when the simulator shifts to a newer ROS2 version.

[F1Tenth ROS2 Simulator repo](https://github.com/f1tenth/f1tenth_gym_ros/tree/main)

Follow the steps till "Launching the Simulation" from the README of the above repo.

If this is you are installing this for the first time, go ahead and launch the simulation using 
```
$ source /opt/ros/foxy/setup.bash
$ source install/local_setup.bash
$ ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```
to check if it is working as intended or not. 

You should see a car in a simulation environment on the screen.

The following steps need to be followed whenever you are working with the F1Tenth simulator after closing everything.

The below command needs to be executed only once in a session.
`docker compose up`

The below command needs to be executed in every new instance of a terminal
`docker exec -it f1tenth_gym_ros-sim-1 /bin/bash`

The next two commands need to be run in every new instance of a terminal to ensure that the `ros2` command is recognized.

```
$ source /opt/ros/foxy/setup.bash
$ source install/local_setup.bash
```

To not have to do this everytime, add the above commands to your .bashrc using
```
$ echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
$ echo "source install/local_setup.bash" >> ~/.bashrc
```

Follow the steps from [3](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html#check-environment-variables) onwards to configure the environment variables required by ROS2 in the container.

1. Installing `turtlesim`
    Follow the steps from [here](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html#install-turtlesim) to install turtlesim.

2. Starting `turtlesim`
`ros2 run turtlesim turtlesim_node`

Create a new instance of a terminal, or split the xterminator.

3. Use `turtlesim`
`ros2 run turtlesim turtle_teleop_key`

Create another instance of terminal.

4. Installing `rqt`
    Follow the steps from [here](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html#install-rqt)

5. Use `rqt`
    Follow the steps from [here](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html#use-rqt)

Create another instance of terminal.

6. Remapping / Controlling another turtle
`ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel`

At this point you should have $5$ instances of terminals running.
1. Docker Container
2. `turtlesim_node`
3. `rqt`
4. `turtlesim_teleop_key` for turtle1
5. `turtlesim_teleop_key` for turtle2

To close the entire application, use `q` in the terminals running `turtlesim_teleop_key`, `Ctrl + C` in $2$ and $3$.

To exit from the container and return to local system, use `exit`