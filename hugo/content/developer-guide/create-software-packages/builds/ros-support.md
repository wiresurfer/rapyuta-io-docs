---
title: "ROS Support"
description:
type: developer-guide
date: 2019-10-25T12:39:37+05:30
pre: "b. "
weight: 325
---
You can control how ROS packages will be built by specifying catkin
build parameters. rapyuta.io provides a handful of catkin build
parameters when adding a ROS package. They are:

1. **ROS packages**    
A list of ROS packages in the catkin workspace that you want to build.    
The ROS package name must begin with an alphabet (A-Z, a-z), followed by alphanumeric
characters (A-Z, a-z, 0-9) or an underscore ( _ ) or at most one forward slash ( / )
2. **Blacklist**     
A list of ROS packages in the catkin workspace that you do not want to build even
if another package depends on it.    
The ROS package name must begin with an alphabet (A-Z, a-z), followed by alphanumeric
characters (A-Z, a-z, 0-9) or an underscore ( _ ) or at most one forward slash ( / )
3. **Make arguments**    
A list of make options that you intend to use while building the ROS package.
4. **CMake arguments**    
A list of cmake options that you want to use while building the ROS package.
5. **Catkin Make arguments**    
A list of make options that you want to use while building ROS packages.

The catkin build parameters are optional. If you choose to not specify any of them,
the ROS Builder will build all ROS packages in its catkin workspace.

The context directory is a specific project directory (folder) relative to the
git repository. It is copied to the ROS Builder's catkin workspace, and
subsequently, catkin build parameters are applied to it. In the absence of a
context directory, all of the folders in the git repository are built.

To add a set of catkin build parameters, click **Add Parameter** against
**CATKIN BUILD PARAMETERS** while adding a package using rapyuta.io

You may provide multiple sets of catkin build parameters for a single ROS package,
thus you can run multiple catkin builds on a ROS package.

![Catkin build parameters](/images/core-concepts/packages/multiple-sets-catkin-build-params.png?classes=border,shadow&width=50pc)