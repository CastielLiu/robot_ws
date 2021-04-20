
# gmapping demo
roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch     #gazabo (environment_model/robot_model/sensor_model  )
roslaunch mbot_navigation gmapping_demo.launch         #gmapping

roslaunch mbot_teleop mbot_teleop.launch               #tele_control
rosrun map_server map_saver -f map                     #save_map

#navigation demo
roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
roslaunch mbot_navigation nav_cloister_demo.launch

# exploring_slam
roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
roslaunch mbot_navigation exploring_slam_demo.launch  #gmapping+movebase we can use 2D Nav Goal to exploring_slam

#auto exploring_slam
roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
roslaunch mbot_navigation exploring_slam_demo.launch  #gmapping+movebase
roslaunch explore_lite explore.launch                 #sudo apt-get install ros-kinetic-explore-lite


#amcl resample all partials
rosservice call /global_localization "{}"


