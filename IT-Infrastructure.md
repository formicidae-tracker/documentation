FORT is designed to allow a remote monitoring of multiple experiments running in parallel, to save space in the experiment room and at the same time offer a simple and modular hardware setup. The resulting IT infrastructure is explained in the chart below.

<img alt="IT Infrastructure overview" src="/home/matthias/Documents/fomicidae-tracker/documentation/images/network_explained.png" width="300" />

## Local tracking network
A local network (pink lines, give the protocol) connects all the tracking host via the switch. In the master-slave configuration, several slave hosts can be daisy-chained to a master via the frame-grabber directly to improve the frame rate (blue line, for more information see xx). Each of the n hosts then processes only every n-th frame and ends the tracking data to the master via the network. There, the data is assembled and written to the output file.
[[Software Architecture]] describes how this process is coordinated.

## Master - slave configuration
The experiment is controlled by the master host, providing the trigger for the camera and IR flashes (blue line). It also launches, queries the state of and stops the climate control on the **zeus** board by providing a set-point for the current ambient conditions during the experiment (red line). For detailed information, see [[User Guide: Controlling Climate|User-Guide:-Controlling-Climate]].

## Setup PCs
Unless an experiment is being set up, there are no monitors and input devices required in the experiment room. The tracking hosts are equipped with an HDMI dongle that, upon reboot, simulates the presence of a screen. The display manager service will therefore be running, which allows remote desktop access from the setup computers.

Any PC that meets the basic requirements can be connected to the local network to be used as a setup computer (see [[User Guide: Starting a tracking experiment]]). Several PCs can be connected to the local network allowing to configure experiments simultaneously.
This allows users to prepare and preserve their configuration files on private laptops.

## Gateway
The gateway computer separates the local tracking network from the internet and hosts the **olympus** webapp that displays climate data, warnings and errors. It also provides the ports for the web streaming of the tracking video output.

# Conclusion
* To setup an experiment, the user needs a setup PC and access to the local tracking network switch.
* SSH connections to tracking hosts are only possible from within the local tracking network.
* VNC (remote desktop) connections are only possible from withing the local tracking network.
* Climate data can be monitored in real time via the **olympus** webapp.
* Using a network streaming application (e.g. VLC-video player) it is possible to observe the tracking video output in with a delay.
* The real time video stream of an experiment can only be obtained locally on the corresponding tracking host, when connected to it via VNC.
* There is no way to access a tracking host from outside the local tracking network and so it is not possible to start or stop a tracking experiment or access the output data without being connected to that network.
* The FORT design *as is* does not implement a backup strategy of the data produced on the hosts.
