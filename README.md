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


### Patches

In the workspace root directory run,

```sh
git apply --directory=src/hratc2017_framework patches/hratc_framework.patch
git apply --directory=src/hratc2017_robot patches/hratc_robot.patch
```
