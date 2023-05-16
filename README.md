Install firmware
------------

###### [download Orangepizero2_3.0.6_ubuntu_jammy_server_linux5.16.17.7z](https://drive.google.com/file/d/1bOtd9FwgLO2Cj4SauVdK410bDGqvtwhP/view?usp=share_link "download Orangepizero2_3.0.6_ubuntu_jammy_server_linux5.16.17.7z")

	sudo nano /etc/apt/sources.list
	sudo apt update
	sudo apt upgrade

	sudo apt install xvfb
	sudo apt-get install python3-pip glslang-tools meson ninja-build
	sudo apt install bc python3-pip flex bison build-essential libncurses5-dev

	pip3 install setuptools mako
	sudo apt build-dep mesa libdrm

	wget https://archive.mesa3d.org/mesa-23.1.0.tar.xz
	tar -xf mesa-23.1.0.tar.xz
	cd mesa-23.1.0
	meson setup build-mesa/ -Dgallium-drivers=panfrost -Dtools=drm-shim -Dvulkan-	drivers=panfrost -Dllvm=disabled
	ninja -C build-mesa/
	sudo ninja -C build-mesa/ install

Add remote desktop
------------

	sudo apt-get install mesa-utils
	apt-get install  xfonts-base

	apt-get install x11-xserver-utils
	sudo apt-get install tightvncserver
	vncserver
	vncserver -kill :1
	touch /home/orangepi/.Xresources
	sudo apt-get install lxde-core

	nano ~/.vnc/xstartup

	#!/bin/sh
	xrdb "$HOME/.Xresources"
	xsetroot -solid grey
	export XKL_XMODMAP_DISABLE=1
	/etc/X11/Xsession
	startlxde &


