# Fanuc

[![Github Issues](https://img.shields.io/github/issues/ros-industrial/fanuc.svg)](http://github.com/ros-industrial/fanuc/issues)

[![license - BSD-3-Clause](https://img.shields.io/:license-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

[![support level: community](https://img.shields.io/badge/support%20level-community-lightgray.svg)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)


ROS-Industrial Fanuc support.


## Contents

Branch naming follows the ROS distribution they are compatible with.

For ROS 2, the default branch is `ros2`, which targets Rolling.
Only in cases where bw-compatibility would otherwise be broken will additional distribution-specific branches be created.

In other words: the `ros2` branch is expected to be compatible with Foxy, Humble, Iron and Rolling at this time.

### MoveIt configurations

No MoveIt configuration packages are provided at this time.


## Status

The packages in this repository are *community supported*.
This means they do not get support from the OEM, nor from the ROS-Industrial consortia directly (see also the `support level` badge at the top of this page).

Maintenance and development is on a best-effort basis and depends on volunteers.

If you are looking for official support, ask your local Fanuc branch office for their version of the ROS 2 Fanuc driver.


## Installation

The packages in this repository have not yet been released onto the ROS buildfarm.
This means they will have to be built from source in a Colcon workspace.

Refer to the *Building* section below.


## Building

### On newer (or older) versions of ROS 2

Building the packages on newer (or older) versions of ROS 2 is in most cases possible and supported.

For example: building the packages in this repository for ROS Iron or ROS Humble is supported.
This will require creating a Colcon workspace, cloning this repository, installing all required dependencies and finally building the workspace.

### Building the packages

The following instructions assume a Colcon workspace has been created at `$HOME/colcon_ws` and the *source space* is at `$HOME/colcon_ws/src`.
Update paths where appropriate if they are different on the build machine.

These instructions build the `ros2` branch on a ROS Rolling system:

```bash
# make sure the base ROS installation is activated
source /opt/ros/rolling/setup.bash

# change to the root of the Colcon workspace
cd $HOME/colcon_ws

# retrieve the latest development version of fanuc
git clone -b ros2 https://github.com/ros-industrial/fanuc.git src/fanuc

# check build dependencies. Note: this may install additional packages,
# depending on the software installed on the machine
rosdep update

# be sure to change 'rolling' to whichever ROS release you are using
rosdep install --from-paths src/ --ignore-src --rosdistro rolling

# build the workspace
colcon build
```

### Activating the workspace

Finally, activate the workspace to get access to the packages just built:

```bash
$ source $HOME/colcon_ws/install/local_setup.bash
```

At this point all packages should be usable (ie: `ros2 launch` should be able to auto-complete package names starting with `fanuc_..`).
In case the workspace contains additional packages (ie: not from this repository), those should also still be available.


## Installation and usage

The support packages in this repository can be used just as other ROS 2 packages providing robot descriptions (ie: meshes, URDFs/xacros).

To quickly view a specific robot model, `ros2 launch` the provided `view_<robot_model>.launch` file.


## Disclaimer

The author(s) of these packages is (are) not affiliated with FANUC Corporation in any way.
All trademarks and registered trademarks are property of their respective owners, and company, product and service names mentioned in this readme or appearing in source code or other artefacts in this repository are used for identification purposes only.
Use of these names does not imply endorsement by FANUC Corporation.
