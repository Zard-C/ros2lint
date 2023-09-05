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

## Docker

The Docker Image is available on Docker Hub. It's based on `Ubuntu 20.04` and `ROS2 Humble`.

[Docker Hub](https://hub.docker.com/repository/docker/tonghezhang/ros2_x86/general)

```bash
docker pull tonghezhang/ros2_x86:humble_lint_0.2
```

### Run

example:

```bash
sudo docker run --shm-size=1024m --name ros2_humble_lint --privileged -it -d -p 2337:22 -p 4907:4000 -v /Users/zhangtonghe/share:/share   tonghezhang/ros2_x86:[tag]   /bin/bash
```

### Limitation

0. The Docker Image is based on `Ubuntu 20.04` and `ROS2 Humble`. It's not possible to run the image on a host with a different OS or ROS2 version.

1. Using `iceoryx` as the RMW implementation is not always supported due to [#1776](https://github.com/eclipse-iceoryx/iceoryx/issues/1176), so we recommand `rmw_fastrtps_cpp` as the default RMW implementation. But you can find a solution in [#1776](https://github.com/eclipse-iceoryx/iceoryx/issues/1176) to use `iceoryx` as the RMW implementation.

### Docker update record

[Update Record](doc/UpdateRecord.md)
