---
layout: default
title: Mapping
nav_order: 3
has_children: false
---

# Mapping
{: .no_toc }

This section will go over the different methods of mapping possible with the quadcopter.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## Gmapping with Teleop

These instructions work with both ROS Kinetic and Melodic.

Make sure `use_ground_truth_for_tf` is set to `true` in the `quadcopter_gazebo/quadcopter.launch` file.

In Terminal Tab 1:

```bash
# Runs the Gazebo world
roslaunch quadcopter_gazebo quadcopter.launch
```

In Terminal Tab 2:

```bash
# Runs the rviz visualization tool and gmapping node which creates a map of the environment
roslaunch quadcopter_mapping quadcopter_gmapping.launch
```

In Terminal Tab 3:

```bash
# Runs the code for hovering the drone
roslaunch quadcopter_takeoff_land quadcopter_takeoff_land.launch
```

In Terminal Tab 4:

```bash
# Runs the code for controlling the drone with keyboard
roslaunch quadcopter_teleop quadcopter_teleop.launch
```

After Mapping in Terminal Tab 5:

```bash
# Saves the map to the desired directory
rosrun map_server map_saver -f /home/<username>/catkin_ws/src/quad_sim/quadcopter_mapping/maps/new_map
```

After map has been saved, land the drone in Terminal Tab 6:

```bash
# Lands the drone
rostopic pub /quadcopter_land -r 5 std_msgs/Empty "{}"
```

Now, you can close all terminal tabs with `CTRL-C`.

---

## Gmapping with Frontier Exploration

At the moment, these instructions will only work for ROS Kinetic. I am getting it to work for ROS Melodic.

Make sure `use_ground_truth_for_tf` is set to `true` in the `quadcopter_gazebo/quadcopter.launch` file.

In Terminal Tab 1:

```bash
# Runs the Gazebo world
roslaunch quadcopter_gazebo quadcopter.launch
```

In Terminal Tab 2:

```bash
# Runs the code for hovering the drone
roslaunch quadcopter_takeoff_land quadcopter_takeoff_land.launch
```

In Terminal Tab 3:

```bash
# Runs the code for frontier exploration, rviz, gmapping, and move_base
roslaunch quadcopter_exploration quadcopter_exploration.launch
```

After Mapping in Terminal Tab 4:

```bash
# Saves the map to the desired directory
rosrun map_server map_saver -f /home/<username>/catkin_ws/src/quad_sim/quadcopter_mapping/maps/new_map
```

After map has been saved, land the drone in Terminal Tab 5:

```bash
# Lands the drone
rostopic pub /quadcopter_land -r 5 std_msgs/Empty "{}"
```

Now, you can close all terminal tabs with `CTRL-C`.

---

## Google Cartographer with Teleop

These instructions only work with ROS Melodic.

Make sure `use_ground_truth_for_tf` is set to `false` in the `quadcopter_gazebo/quadcopter.launch` file.

In Terminal Tab 1:

```bash
# Runs the Gazebo world
roslaunch quadcopter_gazebo quadcopter.launch
```

In Terminal Tab 2:

```bash
# Runs the rviz visualization tool and cartographer node which creates a map of the environment
roslaunch quadcopter_mapping quadcopter_cartographer.launch
```

In Terminal Tab 3:

```bash
# Runs the code for hovering the drone
roslaunch quadcopter_takeoff_land quadcopter_takeoff_land.launch
```

In Terminal Tab 4:

```bash
# Runs the code for controlling the drone with keyboard
roslaunch quadcopter_teleop quadcopter_teleop.launch
```

After Mapping in Terminal Tab 5:

```bash
# Saves the map to the desired directory
rosrun map_server map_saver -f /home/<username>/catkin_ws/src/quad_sim/quadcopter_mapping/maps/new_map
```

After map has been saved, land the drone in Terminal Tab 6:

```bash
# Lands the drone
rostopic pub /quadcopter_land -r 5 std_msgs/Empty "{}"
```

Now, you can close all terminal tabs with `CTRL-C`.
