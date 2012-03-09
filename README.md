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
#### Install rosinstall (if not already install):

    sudo apt-get install python-setuptools
    sudo easy_install -U rosinstall

#### Download IS4S ROS code, rosjava, rosjava.android, appmanandroid, and example apps

    rosinstall $ROS_WORKSPACE "https://raw.github.com/GAVLab/is4s_ros_pkg/master/android_all.rosinstall"
    source setup.bash

#### Patch rosjava_core

    roscd is4s_esr_android/mods
    ./apply_patch

    
#### Build apps (use --threads=1 to prevent an error from a race condition http://code.google.com/p/rosjava/issues/detail?id=63 ):

    rosmake rosjava_core --threads=1
    rosmake android_teleop --threads=1


### Build the IS4S ESR project:

    rosmake is4s_esr_teleop --threads=1

## Running the applications:

### Start the emulator:

    emulator -avd 'AVD_NAME'

### Install the compiled app (*.apk) to the emulator:

    adb install APP_NAME.apk