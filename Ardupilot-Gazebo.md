# INSTALL ARDUPILOT
[Ardupilot Install Source](https://github.com/Intelligent-Quads/iq_tutorials/blob/master/docs/Installing_Ardupilot_20_04.md)

### Clone Ardupilot 
```sh
cd ~
sudo apt install git
git clone https://github.com/ArduPilot/ardupilot.git
cd ardupilot
```

### Install dependencies
```sh
cd ardupilot
Tools/environment_install/install-prereqs-ubuntu.sh -y
```

Reload profile
```sh
. ~/.profile
```

### If the next step `git submodule update` fails
```sh
git config --global url.https://.insteadOf git://
```

### For Ubuntu 20.04, Checkout Latest Copter Build
```sh
git checkout Copter-4.4.0
git submodule update --init --recursive
```

### For Ubuntu 22.04, Checkout Latest Copter Build
```sh
git checkout Copter-4.5.0
git submodule update --init --recursive
```

Run SITL (Software In The Loop) once to set params:
```sh
cd ~/ardupilot/ArduCopter
sim_vehicle.py -w
```

### Notes
- if `sim_vehicle.py: command not found`, try to restart your laptop.

<br>

# INSTALL GAZEBO AND GAZEBO PLUGIN 
[Gazebo & Plugin Install Source](https://github.com/Intelligent-Quads/iq_tutorials/blob/master/docs/installing_gazebo_arduplugin.md)

### Install Gazebo Plugin
```sh
cd ~
git clone https://github.com/khancyr/ardupilot_gazebo.git
cd ardupilot_gazebo
```

build and install plugin 
```sh
mkdir build
cd build
cmake ..
make -j4
sudo make install
```
```sh
echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
```

set path for models:
```sh
echo 'export GAZEBO_MODEL_PATH=~/ardupilot_gazebo/models' >> ~/.bashrc
. ~/.bashrc
```

<br>

# HOW TO RUN SIMULATOR
### Run gazebo in Terminal 1
```sh
gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world
```

### Run SITL in Terminal 2
```sh
cd ~/ardupilot/ArduCopter/  
sim_vehicle.py -v ArduCopter -f gazebo-iris --console
```
