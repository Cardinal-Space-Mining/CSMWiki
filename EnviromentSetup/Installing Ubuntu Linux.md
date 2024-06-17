This guide will walk you through setting up a windows machine for use with CSM and ROS2 Humble. If you follow it exactly, this will make the exact type of laptop that we use in mission control. This best works with a windows machine, but other OS's should be able to follow along and install what is needed.

CSM uses Ubuntu Linux Jammy Jellyfish to run ROS2, so the first decision you need to make is to dual boot or to use a VM. 

Ros2 has a feature where all machines that are on the same network talk to one another. This is useful, especially when sending joystick commands from the laptop in mission control to the robot in the arena. Booting a native instance of Ubuntu is the best way to get this functionality, as virtualization techniques tend to impair it. The downside is that it is more involved to setup.

For virtualization options, WSL is recommended for windows machines, and VMBox is recommended for non-windows machines.

Note, regardless of which option you choose, 50GB+ is the recommended amount of drive space to allocate to an Ubuntu instance for CSM purposes. I personally allocated 100GB, though you can get away with less.

## Dual Boot (For Mission Ctrl Machines):
1. [Here](https://gcore.com/learning/dual-boot-ubuntu-windows-setup/) is a great tutorial on the subject
2. Get a copy of a Ubuntu Jellyfish ISO, found [here](https://releases.ubuntu.com/jammy/)
3. Install a copy of Rufus found [here](https://rufus.ie/en/)
4. Click restart in windows and hold shift while it restarts to boot into recovery mode
5. Click Use a device
6. Select the Ubuntu install USB you made
7. Install Ubuntu
## Windows Subsystem For Linux
1. From an elevated command prompt, run `wsl --install Ubuntu` 
2. Ubuntu should be installed by default

## VMBox (For non windows machines or advanced needs)
1. Install VMBox from [here](https://www.virtualbox.org/)
2. Get a copy of a Ubuntu Jellyfish ISO, found [here](https://releases.ubuntu.com/jammy/)
3. Follow [this](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview) tutorial

