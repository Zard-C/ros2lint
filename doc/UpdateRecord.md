# Docker Update Record

## 2023-09-03

### Update230903

1. install clang
2. add `colcon build --packages-up-to rclc`, we have rclc installed now.

docker image: `tonghezhang/ros2_x86:humble_lint_0.1`

## 2023-09-04

### Update230904

1. install rmw_cyclonedds_cpp and rmw_iceoryx_cpp
2. add `colcon build --packages-up-to rmw_cyclonedds_cpp --packages-up-to rmw_iceoryx_cpp`, we have rmw_cyclonedds_cpp and rmw_iceoryx_cpp installed now.
3. add `demo_nodes_cpp` for testing.

docker image: `tonghezhang/ros2_x86:humble_lint_0.2`

#### How to fix the problem of rmw_iceoryx_cpp

Due to issue [#1776](https://github.com/eclipse-iceoryx/iceoryx/issues/1176)

> To solve this problem locally yourself you could try to copy the file `iceoryx_hoofs/platform/win/include/iceoryx_hoofs/platform/acl.hpp` to
> `iceoryx_hoofs/platform/linux/include/iceoryx_hoofs/platform/acl.hpp`.
>
> In Windows we do not support ACLs at all and replaced the libacl implementation with a stub implementation.
> When you copy the windows acl.hpp file to the linux platform then linux would as well use the stub implementation of windows. It is like turning of ACLs.

### Update230907

1. build a debug version using `colcon build --ament-cmake-args -DCMAKE_BUILD_TYPE=Debug`
2. install gdb

docker image: `tonghezhang/ros2_x86:humble_lint_debug`
