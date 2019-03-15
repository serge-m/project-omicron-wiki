# How To ...

1. ... install OS on the SD card?

We use Linux Ubiquity Xenial LXDE distro as our main OS. To install it, you need:
 - download the archive with latest build from here: https://downloads.ubiquityrobotics.com/pi.html
 - to write OS to SD card we use Etcher. It is free, and you can get it from here: https://www.balena.io/etcher/
 - you also need a card reader

The rest is straitforward, insert SD card in your PC, start the Etcher, select the Ubiquity Xenial LXDE and start the installation.
Once the installation is finished, your SD card is ready to run on the Raspberry Pi.

2. ... write the launch file to start the car?

To start the node we provide the launch file for each node. But the question is how to start all nodes with 1 launch file.
It is very straitforward. Once you have all nodes in your workspace you need to run from the catkin workspace root directory: 
```catkin_make install```
```source devil/setup.sh```
Afterwards you can create the launch file in the catkin workspace with the following syntax
```
<launch>
	<include file="$(find <pkg name 1>)/path/to/file.launch" />
	<include file="$(find <pkg name 2>)/path/to/file.launch" />
</launch>
```