# loam_continuous

This is a LOAM (Lidar Odometry and Mapping) ROS package for continuous rotating 2D laser scanner. This package is a simple modified copy of the original one release by [Ji Zhang](http://www.frc.ri.cmu.edu/~jizhang03/). The only change on top of the original one is to make it a Catkin package and work under ROS Indigo. Please cite their paper if this package is used. 

J. Zhang and S. Singh. LOAM: Lidar Odometry and Mapping in Real-time. Robotics: Science and Systems Conference (RSS). Berkeley, CA, July 2014.([PDF](http://www.frc.ri.cmu.edu/~jizhang03/Publications/RSS_2014.pdf))([VIDEO](https://www.youtube.com/watch?feature=player_embedded&v=8ezyhTAEyHs))

Wiki Webpage by the Author: [http://wiki.ros.org/loam_continuous](http://wiki.ros.org/loam_continuous)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=8ezyhTAEyHs
" target="_blank"><img src="http://img.youtube.com/vi/8ezyhTAEyHs/0.jpg" 
alt="LOAM back and forth" width="240" height="180" border="10" /></a>

# how to use
Here I assume you have a Catkin worksapce under ~/ros_workspace/catkin_ws.

(1) gitclone the package into your "src" folder.
+ **cd ~/ros_workspace/catkin_ws/src**
+ **git clone https://github.com/daobilige-su/loam_continuous**

(2) compile the package
+ **cd ~/ros_workspace/catkin_ws**
+ **catkin_make**

(3) download a ROS bag file for test dataset.
+ **roscd loam_continuous**
+ **mkdir data**
+ download [robot_city_bridge](www.frc.ri.cmu.edu/~jizhang03/Datasets/robot_city_bridge.bag) dataset into your ~/ros_workspace/catkin_ws/src/loam_continuous/data/ folder.

(4) run the package and rosbag file
+ 1) in 1st terminal:
+ **roslaunch loam_continuous loam_continuous.launch**
+ 2) in 2nd terminal:
+ **roscd loam_continuous/data/**
+ **rosbay play robot_city_bridge.bag**
+ (use -r 0.5 if the result look bad and it is due to the less powerful CPU, (e.g. rosbay play robot_city_bridge.bag -r 0.5))

YOU SHOULD SEE A RESULT SIMILAR TO THEIR DEMO VIDEO ([robot_city_bridge DEMO VIDEO](http://www.frc.ri.cmu.edu/~jizhang03/Videos/robot_city_bridge.mp4). GOOD LUCK.

# Original Introduction by the author:

Laser Odometry and Mapping (Loam) is a realtime method for state estimation and mapping using a 3D lidar. The program contains two major threads running in parallel. An "odometry" thread computes motion of the lidar between two sweeps, at a higher frame rate. It also removes distortion in the point cloud caused by motion of the lidar. A "mapping" thread takes the undistorted point cloud and incrementally builds a map, while simultaneously computes pose of the lidar on the map at a lower frame rate. The lidar state estimation is combination of the outputs from the two threads.

If an IMU is available, the orientation (integrated from angular rate) and acceleration measurements are used to deal with general motion of the lidar, while the program takes care of the linear motion.

The program is tested on a laptop with 2.5 GHz quad cores and 6 Gib memory (the program consumes two cores). It uses a continuous spin lidar.

Wiki Webpage: http://wiki.ros.org/loam_continuous

