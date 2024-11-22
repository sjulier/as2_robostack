# Aerostack2 in Robostack

> [!NOTE]  
> This Readme is a temp version, it's currenlty link to the forked version from Simon.

This project hopefully will allow you to install and run aerostack2 from within [Robostack](https://robostack.github.io/GettingStarted.html)

## Installation

### Creating the Environment

I would recommend you install `micromamba` or `mamba`

> If you install `micromamba`, then would recommend adding `alias mamba=micromamba` to your environment variable

Then find a workspace and clone this repository 

```
git clone --recursive https://github.com/sjulier/as2_robostack.git 
cd as2_robostack
mamba env create -f environment.yaml
```

This will create an environment called `aerostack2`

To start the environment use the command

```
mamba activate aerostack2
```

### Aerostack2

To build everything, in this repository now run the following

```
colcon build --symlink-install  --cmake-args -DPython3_FIND_VIRTUALENV=ONLY --packages-ignore as2_realsense_interface
```

<!-- Adam: Unsure about this, I don't have this error -->
> Note: It may fail the first time this command is run due to a `x86_64-conda-linux-gnu-c++: fatal error: Killed signal terminated program cc1plus
compilation terminated.` I have found that just running the command again continues the build... 

#### tmuxinator
Finally in order to run some aerostack projects, we need to install `tmuxinator`. We install using Ruby.

<!-- Adam: I haven't tried local version, I just used via homebrew, I don't know the benifit of local version. -->
Using a Mac, it is better to install a local version:
- Local version
    ```
    brew install ruby
    ```

    Follow the instructions for .zshrc and open a new shell.

    ```
    gem install tmuxinator
    ln -s "$CONDA_PREFIX/bin/ruby" "$CONDA_PREFIX/share/rubygems/bin/ruby"
    ```
- Via homebrew
    ```
    brew install tmuxinator
    ```

### Post Installation
> [!NOTE]  
> This is still a bit too complex, will need to simplify this.
We need to source bash script
We need to configure bash to configure mamba environment and as2_cli environment
```
mamba activate aerostack2
# PATH TO WORKSPACE
export AEROSTACK2_PATH=$HOME/WorkSpace/as2_robostack/src/aerostack2 
source $AEROSTACK2_PATH/as2_cli/setup_env.bash
```

## Running

We are going to be running the following [aerostack2 gazebo project](https://aerostack2.github.io/_02_examples/gazebo/project_gazebo/index.html)

Follow the example there, but I would recommend you clone the project into this repository:

```
git clone https://github.com/aerostack2/project_gazebo
```

<!-- > Note: Remember to `source install/setup.bash` before running anything -->



