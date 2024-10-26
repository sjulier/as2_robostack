# Aerostack2 in Robostack

This project hopefully will allow you to install and run aerostack2 from within [Robostack](https://robostack.github.io/GettingStarted.html)

## Installation

### Creating the Environment

I would recommend you install `micromamba` or `mamba`

> If you install `micromamba`, then would recommend adding `alias mamba=micromamba` to your environment variable

Then find a workspace and clone this repository 

```
git clone <>
cd as2_robostack
mamba create -f environment.yaml
```

This will create an environment called `aerostack2`

To start the environment use the command

```
mamba activate aerostack2
```

### Aerostack2

Now clone in aerostack2. Run the following from this repository. (Make sure you put them in `src` folder)

```
git clone https://github.com/aerostack2/aerostack2.git src/aerostack2
git clone https://github.com/MOCAP4ROS2-Project/mocap4r2_msgs.git src/mocap4r2_msgs
```

> TODO: Add as submodue

There are a couple of things to change, therefore copy the following files into aerostack2

```
cp modifications/CMakeLists.txt src/aerostack2/as2_core/

cp modifications/detect_aruco_markers_behavior.cpp src/aerostack2/as2_behaviors/as2_behaviors_perception/detect_aruco_markers_behavior/src/
```

To build everything, in this repository now run the following

```
colcon build --symlink-install --packages-ignore as2_rviz_plugins
```

Finally in order to run some aerostack projects, we need to install `tmuxinator`. We install using Ruby:

```
gem install tmuxinator
```

## Running

We are going to be running the following [aerostack2 gazebo project](https://aerostack2.github.io/_02_examples/gazebo/project_gazebo/index.html)

Follow the example there, but I would recommend you clone the project into this repository:

```
git clone https://github.com/aerostack2/project_gazebo
```




