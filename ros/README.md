# f1tenth_decription
All files concerning the simulated robot, i.e. meshes, xacro, urdf, and usd.

## Importing the robot urdf into Isaac Sim

When importing it is important that file path to the meshes are correct in the urdf file. The file path should be relative to the urdf file. E.g.:

```xml
  <link name="base_link">
    <visual>
      <origin rpy="0 0 0" xyz="0 0 0"/>
      <geometry>
        <mesh filename="file:///<YOUR_PATH>/f1tenth_decription/src/Assembly_description/meshes/base_link.stl"/>
      </geometry>
    </visual>
  </link>
```

## Configuring the and importing using the URDF Importer tool in Isaac Sim

1. Open the URDF Importer tool in Isaac Sim
2. Click "Add URDF" and select the .urdf file
3. Unitick ... something
4. Click "Import"

## Building this package

If you want to build this package, you need to have ROS1 installed to use `catkin_make`. It is recommended to install distrobox and then install the ROS noetic image:
  
  ```bash
  distrobox create -n ros-noetic -i docker.io/osrf/ros:noetic-desktop-full
  ```

  Then you can start the container with:

  ```bash
  distrobox enter ros-noetic
  ```

  Then you can build the package with:

  ```bash
  cd /path/to/f1tenth_description
  catkin_make
  ```

  Now you can generate the .urdf file from the .xacro file with:

  ```bash
  rosrun xacro xacro src/Assembly_description/urdf/Assembly.xacro > f1tenth.urdf
  ```

## Remember!

```bash
cd ~/f1tenth_description/src
catkin_init_workspace
cd ..
catkin_make
source devel/setup.bash
```