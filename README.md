### Generic Lidar
## This project is currently a WIP and not intended for use yet
This project is heavily influences from the [Velodyne Gazebo model tutorial](http://gazebosim.org/tutorials?tut=guided_i1). The main difference is that the format has been converted to the .xacro format and many of the different properties of the lidar have been pulled out into variables with appropriate calculations taking place based on those parameters. This gives you the ability to easily tweak these input parameters in order to match the specs of various different lidar units.

The model is defined in the .xacro format. In order to generate a urdf run the following command (note: this assumes you have the ros kinetic packages installed).

```
rosrun xacro xacro generic_lidar.xacro --inorder > generic_lidar.urdf
```

A new urdf file called generic_lidar.urdf will be generated. If you would like to convert this to an sdf file for gazebo you can run the following command (requires [gazebo](http://gazebosim.org/download)).

```
gz sdf -p generic_lidar.urdf > generic_lidar.sdf
```

An example launch has been included that can show how to spawn this model within a gazebo simulation. In order to run this model directly in gazebo clone the repo into the src directory of a catkin workspace. Make sure you have ran source devel/setup.bash and then you can run the following command:

```
roslaunch generic_lidar test_lidar.launch
```

A gazebo plugin has been added to allow communication through ROS. It is already set to be included in the launch file. First build the plugin and add it to the gazebo plugin directory.

```
cd generic_lidar/plugins
mkdir build
cd build
cmake ..
make
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:[PATH_TO_THE_BUILD_FOLDER_YOU_JUST_CREATED]
```