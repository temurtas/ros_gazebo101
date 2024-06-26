------------
Things and scripts to remember
------------
Websites to check

https://wiki.ros.org/ros_control

http://gazebosim.org/tutorials/?tut=ros_control

----------------------------
model files at : Home > .gazebo > models > kobra_mk2  % has a repo at github now ! 

world file  at : Home > kobra_mk2_ws			% has a repo at github now ! 

----------------------------
https://docs.ros.org/en/foxy/Tutorials/Workspace/Creating-A-Workspace.html

rosdep install -i --from-path src --rosdistro foxy -y

https://github.com/ros-simulation/gazebo_ros2_control
https://wiki.ros.org/Ackermann%20Group

----------------------------
ros gazebo plugins at : Computer/opt/ros/foxy/include/gazebo_plugins

- cd ~/kobra_mk2_ws
- rosdep install -i --from-path src --rosdistro foxy -y
- colcon build
- . install/setup.bash

ros2 launch my_teleop teleop_kobra.launch.py

- ros2 run my_teleop my_teleop
- rqt_graph
- ros2 topic echo kobra_mk2/cmd_vel
- ros2 topic echo imu_plugin/out

- remapping (),

----------------------------
- ros2 bag record -o ros_data_2021_06_19_v1 /imu_plugin/out /kobra_mk2/cmd_vel /kobra_mk2/cmd_acc /kobra_mk2/odom /kobra_mk2/distance

- ros2 bag record -o imu_data_only /imu_plugin/out 

----------------------------
Start INS-GPS/Strap Node
- cd ~/INS-GPS-ROS2
- rosdep install -i --from-path src --rosdistro foxy -y
- export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
- colcon build
- . install/setup.bash

- ros2 launch ht_strap_package ht_strap_package.launch.py	% All Nodes

- ros2 launch ht_strap_package ht_only_strap_package.launch.py	% Only Strap Node w/ IMU talker and listener
- ros2 launch ht_strap_package ht_strap_only_ins_gps.launch.py	% Only computational nodes, w/out Talkers

- cd ~/INS-GPS-ROS2 ; rosdep install -i --from-path src --rosdistro foxy -y ; . install/setup.bash; ros2 launch ht_strap_package ht_strap_package.launch.py
- rm -rf ~/INS-GPS-ROS2/imu_strap_data_only ; . ~/INS-GPS-ROS2/install/setup.bash ; ros2 bag record -o ~/INS-GPS-ROS2/imu_strap_data_only /ht_nav_imu_data_topic /ht_nav_strap_topic

----------------------------
Cyclone DDS boot config 
- CYCLONEDDS_URI=file:///boot/cyclonedds_config.xml

----------------------------
Start MATLAB at Ubuntu
- cd MATLAB/R2021b/bin; ./matlab

----------------------------
clear nodes and gzservers
- killall -9 gzserver gzclient
