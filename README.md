### WS setup
Using catkin_tools

```sh
catkin config -a --cmake-args -DCMAKE_EXPORT_COMPILE_COMMANDS=1 -DCMAKE_BUILD_TYPE=Debug
```



### Rosdep
```sh
#rosdep install --reinstall --simulate --from-paths ./src --ignore-src
#since running in singularity instance, run after starting with root privleges
  apt-get install ros-melodic-ros-control
  apt-get install ros-melodic-ros-controllers
  apt-get install ros-melodic-husky-navigation

```
### Rviz
Set `base_link` as ref

### Issue
```sh
Segmentation fault (core dumped)
[gazebo-1] process has died [pid 844885, exit code 139, cmd /opt/ros/melodic/lib/gazebo_ros/gzserver --verbose /home/sj/Projects/ROS/mine_detection_ws/src/hratc2017_framework/description/worlds/softWavyMinefield.world tf:=gazebo_tf __name:=gazebo __log:=/home/sj/.ros/log/8dc2e708-4420-11eb-9e92-44032c8cf37a/gazebo-1.log].
log file: /home/sj/.ros/log/8dc2e708-4420-11eb-9e92-44032c8cf37a/gazebo-1*.log

```
**FIX:**
In the WS run:
```sh
cd ./src/hratc2017_framework/
git apply ../../patches/fix_seg_fault_laser.patch

#Fix the same error in hratc2017_robot too 
cd ./src/hratc2017_robot/
git apply ../../patches/fix_laser_hokuyu.patch 
```
