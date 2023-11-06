## User Guide 
### Available
***
* ros-humble-rom-robot
* ros-humble-rom-robo-driver
* ros-humble-rom-robot-simulation
* ros-humble-rom2109-ai

### 1 How to install ROM Robotics's software?

#### 1.1 Install gpg key and source list
```
$ curl -s --compressed "https://rom-robotics.github.io/romrobotics.repo/dists/rom_robotics.gpg" | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/rom_robotics.gpg >/dev/null
$ sudo curl -s --compressed -o /etc/apt/sources.list.d/rom_robotics.list "https://rom-robotics.github.io/romrobotics.repo/dists/rom_robotics.list"
```
#### 1.2 Install robot driver or some softwares 
```
$ sudo apt update
$ sudo apt install ros-humble-rom-robot
```
#### 1.3 How to remove ?
```
$ sudo apt remove ros-humble-rom-robot
