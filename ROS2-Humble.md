# Robot Operating System 2 (Humble Hawksbill) Installation
<mark>Make sure your Operating System is **Ubuntu 22.04**</mark> <br>
Go to the terminal (Ctrl + Alt + T)

## Set locale
```sh
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

## Setup sources
Ensure that the Ubuntu Universe repository is enabled.
```sh
sudo apt install software-properties-common
sudo add-apt-repository universe
```
Add the ROS 2 GPG key.
```sh
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
Add the repository to your sources list.
```sh
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

## Install ROS2 Packages
```sh
sudo apt update
sudo apt upgrade
sudo apt install ros-humble-desktop
sudo apt install ros-humble-ros-base
sudo apt install ros-dev-tools
```

## Environment Setup 
Do this every time you open the terminal or add it to the <mark>**~/.bashrc**</mark> script
```sh
source /opt/ros/humble/setup.bash
```

# MAVROS Installation
