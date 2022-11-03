FROM osrf/ros:galactic-desktop

# use bash instead of sh
SHELL ["/bin/bash", "-c"]
ENV DEBIAN_FRONTEND=noninteractive


# create workspace
RUN mkdir -p /ros2_ws/src
WORKDIR /ros2_ws

# add packages to path
RUN echo "source /opt/ros/$ROS_DISTRO/setup.bash" >> ~/.bashrc

# TODO - add BNO as a git cloned library in here, then add sudo apt get update and rosdep update
