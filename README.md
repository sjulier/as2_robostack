# Aerostack2 in Robostack

This project hopefully will allow you to install and run aerostack2 from within [Robostack](https://robostack.github.io/GettingStarted.html)

## Installation

### Creating the Environment

I would recommend you install `micromamba` or `mamba`

> If you install `micromamba`, then would recommend adding `alias mamba=micromamba` to your environment variable

Then find a workspace and clone this repository 

```
git clone --recursive https://github.com/mhl787156/as2_robostack 
cd as2_robostack
mamba env create -f environment.yaml
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
cp modifications/CMakeLists.txt src/aerostack2/as2_core/CMakeLists.txt

cp modifications/detect_aruco_markers_behavior.cpp src/aerostack2/as2_behaviors/as2_behaviors_perception/detect_aruco_markers_behavior/src/detect_aruco_markers_behavior.cpp

cp modifications/drone.py src/aerostack2/as2_simulation_assets/as2_gazebo_assets/src/as2_gazebo_assets/models/drone.py
```

To build everything, in this repository now run the following

```
colcon build --symlink-install  --cmake-args -DPython3_FIND_VIRTUALENV=ONLY --packages-ignore as2_rviz_plugins --packages-ignore as2_realsense_interface
```

> The `as2_rviz_plugins` doesn't build right now, will need to figure it out at some point. 

> Note: It may fail the first time this command is run due to a `x86_64-conda-linux-gnu-c++: fatal error: Killed signal terminated program cc1plus
compilation terminated.` I have found that just running the command again continues the build... 

Finally in order to run some aerostack projects, we need to install `tmuxinator`. We install using Ruby.

Using a Mac, it is better to install a local version:

```
brew install ruby
```

Follow the instructions for .zshrc and open a new shell.

```
gem install tmuxinator
ln -s "$CONDA_PREFIX/bin/ruby" "$CONDA_PREFIX/share/rubygems/bin/ruby"
```

## Running

We are going to be running the following [aerostack2 gazebo project](https://aerostack2.github.io/_02_examples/gazebo/project_gazebo/index.html)

Follow the example there, but I would recommend you clone the project into this repository:

```
git clone https://github.com/aerostack2/project_gazebo
```

> Note: Remember to `source install/setup.bash` before running anything



