# ros2lint

How to use a light-weight version of ros2, packages are up to rclc and ros2cli_common_extensions when building from source code.

## Description

This repository demonstrate how to build a `light-weight version of ros2`, packages up to `rclc` and `ros2cli_common_extensions`. It is intended to be used for linting purposes only.

## Install from source code

### Prerequisites

[reference(humble)](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Development-Setup.html)

`TODO`: For specific dependencies, please refer to the Dockerfile.

### Build

Instead of building the entire ros2, we only build the packages we need. In this case we build packages up to rclc and ros2cli_common_extensions.

```bash
colcon build --packages-up-to rclc --packages-up-to ros2cli_common_extensions
```

### Install

We install the packages to a custom location, in this case `install`.

Use a soft link to make the packages available to the system.

```bash
sudo ln -s /path/to/install /opt/ros/${ROS_DISTRO}
```

## Docker Hub

The Docker Image is available on Docker Hub. It's based on `Ubuntu 20.04` and `ROS2 Humble`.
