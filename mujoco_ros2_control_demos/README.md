# mujoco_ros2_control_demos

Demonstration tutorials for the `mujoco_ros2_control` package.
This package provides ready-to-use tutorials that show how to use MuJoCo with ros2_control.

## Documentation

Full tutorial documentation is maintained in RST format:

- **[Demos and Tutorials](doc/tutorials.rst)** — step-by-step tutorials covering basic robot setup, MJCF generation, PID control, transmissions, and the base velocity plugin.

## Quick Start

```bash
# Tutorial 1 – Basic Robot
ros2 launch mujoco_ros2_control_demos 01_basic_robot.launch.py

# Tutorial 2 – MJCF Generation at Runtime
ros2 launch mujoco_ros2_control_demos 02_mjcf_generation.launch.py

# Tutorial 3 – PID Control
ros2 launch mujoco_ros2_control_demos 03_pid_control.launch.py

# Tutorial 4 – Transmissions
ros2 launch mujoco_ros2_control_demos 04_transmissions.launch.py

# Tutorial 5 – Base Velocity Plugin
ros2 launch mujoco_ros2_control_demos 05_base_velocity_plugin.launch.py
```

All tutorials support `headless:=true` to run without the MuJoCo viewer.

## Car demo

The car demo uses a static MJCF generated from its URDF. To regenerate the
model after changing the URDF:

```bash
ros2 run mujoco_ros2_control make_mjcf_from_robot_description.py \
  --save_only \
  --urdf mujoco_ros2_control_demos/demo_resources/car/urdf/car.urdf \
  --output mujoco_ros2_control_demos/demo_resources/car/mjcf
```

Then launch it with:

```bash
ros2 launch mujoco_ros2_control_demos car.launch.py
```

Wheel velocities can be commanded through
`/wheel_velocity_controller/commands` using
`std_msgs/msg/Float64MultiArray`.

For the full list of launch arguments, features, controlling the robot, and package structure, see [`doc/tutorials.rst`](doc/tutorials.rst).

## See Also

- Main package: [mujoco_ros2_control](../mujoco_ros2_control/)
- Tests: [mujoco_ros2_control_tests](../mujoco_ros2_control_tests/)
