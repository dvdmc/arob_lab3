FROM osrf/ros:noetic-desktop-full

# Install dependencies
# python-tk is used by hector rotors GUI
# libtool libtool-bin is used by glog in mav_trajectory_generation
RUN apt-get update && apt-get install -y git tmux vim xterm curl ssh tree python3-catkin-tools python3-tk nano libtool libtool-bin

RUN echo "set -g mouse on" > /root/.tmux.conf

# Create catkin workspace
RUN mkdir -p /root/catkin_ws/src/

# Clone lab repositories
RUN git clone https://github.com/ros-geographic-info/unique_identifier.git /root/catkin_ws/src/unique_identifier && \
    git clone https://github.com/ros-geographic-info/geographic_info.git /root/catkin_ws/src/geographic_info && \
    git clone https://github.com/RAFALAMAO/hector_quadrotor_noetic.git /root/catkin_ws/src/hector_quadrotor_noetic
    
RUN git clone https://github.com/ethz-asl/mav_trajectory_generation.git /root/catkin_ws/src/mav_trajectory_generation && \
    git clone https://github.com/catkin/catkin_simple.git /root/catkin_ws/src/catkin_simple && \
    git clone https://github.com/ethz-asl/eigen_catkin.git /root/catkin_ws/src/eigen_catkin && \
    git clone https://github.com/ethz-asl/eigen_checks.git /root/catkin_ws/src/eigen_checks && \
    git clone https://github.com/ethz-asl/glog_catkin.git /root/catkin_ws/src/glog_catkin && \
    git clone https://github.com/ethz-asl/mav_comm.git /root/catkin_ws/src/mav_comm && \
    git clone https://github.com/ethz-asl/nlopt.git /root/catkin_ws/src/nlopt

# Build catkin workspace to check that everything works
RUN /bin/bash -c '. /opt/ros/noetic/setup.bash && cd /root/catkin_ws && catkin build'
