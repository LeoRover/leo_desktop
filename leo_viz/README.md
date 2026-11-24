## Overview

This package provides launch files and
[rviz](https://index.ros.org/p/rviz) configurations for visualizing
[Leo Rover](Robots/Leo Rover) (real or a simulated one) from a desktop
environment.

## Usage

To view the Leo Rover model without having the real or simulated robot
connected to the ROS network, use: 

```
roslaunch leo_viz view_model.launch
```



This will run RViz and a basic ROS environment for publishing robot
state, including a GUI for specifying fake joint states (you can disable
the GUI by passing `gui:=false` argument to the launch file).

If you have the robot running on the ROS network and would like to just
visualize it in RViz, type: 

```
roslaunch leo_viz rviz.launch
```



### RViz configurations

If you would like to use a specific RViz configuration, you can add the
`config` argument to the `rviz.launch` file with the configuration
name, for example: 

```
roslaunch leo_viz rviz.launch config:=slam
```

 Here's a list of available
configurations:

  -- --------------------------------------------------------- -- ------------------------------------- -- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --
     <: tablewidth="100%" width="15%"> **config name**      <: width="15%"> **fixed frame**      <:> **description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
     <\^> `robot` (default)                                   <\^ :> `base_link`                   Includes the [RobotModel](https://index.ros.org/p/rviz) display which visualizes the robot model and the [Image](https://index.ros.org/p/rviz) display (disabled by default) for showing images from robot's camera.                                                                                                                                                                                                                                                                                                                                                                                         
     <\^> `odometry`                                          <\^:> `odom`                         Shows the robot model moving according to the position estimated from continuous odometry sources. Adds the [Odometry](https://index.ros.org/p/rviz) display which (when enabled) visualizes the odometry computed by [robot_localization](http://docs.ros.org/en/melodic/api/robot_localization/html/index.html).                                                                                                                                                                                                                                                                                            
     <\^> `slam`                                              <\^ :> `map`                         Shows the robot model in a top-down view with a position that tends to do discrete jumps due to odometry drift correction. Adds the [LaserScan](https://index.ros.org/p/rviz) display to show measurements from laser range-finder and the [Map](https://index.ros.org/p/rviz) display to visualize obstacles detected by [gmapping](https://index.ros.org/p/gmapping). Also adds [Pose](https://index.ros.org/p/rviz) and [PoseArray](https://index.ros.org/p/rviz) displays (disabled by default) that can visualize robot's pose estimated by [amcl](https://index.ros.org/p/amcl) and its uncertainty.   
     <\^> `navigation`                                        <\^ :> `map`                         The same as `slam` configuration, except that it shows costmaps and the navigation plan published by [move_base](https://index.ros.org/p/move_base).                                                                                                                                                                                                                                                                                                                                                                                                                                                        
  -- --------------------------------------------------------- -- ------------------------------------- -- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --

The non-default configurations were created as part of the
[Autonomous Navigation tutorial](https://docs.leorover.tech/development-tutorials/autonomous-navigation)
and won't work with the standard Leo Rover installation.
