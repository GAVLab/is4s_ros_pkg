# IS4S ESR Project

## Installation

### Create a ROS workspace (if you don't have one already):

    mkdir ~/ros_workspace
    cd ~/ros_workspace
    rosws init .

_Note: you can change `~/ros_workspace/` to any path you would like._

### Source the `setup.bash` file to get the ROS_WORKSPACE environment variable up-to-date:

    source setup.bash

### Download and install ROS-Android dependencies (see http://www.ros.org/wiki/ApplicationsPlatform/Clients/Android ): 

#### Download rosjava, rosjava.android, appmanandroid, and example apps

    rosinstall $ROS_WORKSPACE https://kforge.ros.org/appmanandroid/hg/raw-file/tip/appman.rosinstall
    source setup.bash
    
#### Download patch from http://code.google.com/p/rosjava/issues/detail?id=76 and apply:     
    
    patch $ROS_WORKSPACE/rosjava_core/rosjava_bootstrap/android.xml rosjava_core.patch
    
#### Build apps (use --threads=1 to prevent an error from a race condition http://code.google.com/p/rosjava/issues/detail?id=63):

    rosmake rosjava_core --threads=1
    rosmake appmanandroid

### Download the IS4S ESR project with the rosinstall file:

    rosinstall $ROS_WORKSPACE "https://raw.github.com/GAVLab/is4s_ros_pkg/master/is4s_esr.rosinstall"
    source setup.bash

### Build the IS4S ESR project:

