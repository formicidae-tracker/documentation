
Due to the very nature of the tracking system, that has to deal with large amounts of binary data, that need to be distributed in real time between several computers in order to perform online computation, the IT infrastructure has been designed across modular micro services to simplify the development and ease the use of the system. The philosophy of the infrastructure is to have low to none security in any of the standard service (SSH, VNC) or application specific services (Leto, Zeus). Therefore it is advised to run the FORT Setup in a strictly private Local Area Network behind a properly configured firewall.

For the end user this means that any operation (configuration, starting and stopping experiment) on the system has to be performed on site and cannot be done remotely. A webapp has been designed to remotely monitor the setup via a webserver, however, it doesn't allow any control of the system, by design.
The resulting IT infrastructure is explained in the chart below.

<img alt="IT Infrastructure overview" src="https://github.com/formicidae-tracker/documentation/raw/draft-matthias/images/network_explained.png" width="300" />

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
The gateway computer separates the local tracking network from the internet and hosts the **olympus** webapp that displays climate data, warnings and errors. It also provides a streaming webserver to remotely monitor ongoing tracking experiments.

# Conclusion
* To setup an experiment, the user needs a setup PC and access to the local tracking network switch.
* SSH connections to tracking hosts are only possible from within the local tracking network.
* VNC (remote desktop) connections are only possible from withing the local tracking network.
* Climate data can be monitored in real time via the **olympus** webapp.
* Using a network streaming application (e.g. VLC-video player) it is possible to observe the tracking video output in with a delay.
* The real time video stream of an experiment can only be obtained locally on the corresponding tracking host, when connected to it via VNC.
* There is no way to access a tracking host from outside the local tracking network and so it is not possible to start or stop a tracking experiment or access the output data without being connected to that network.
* The FORT design *as is* does not implement a backup strategy of the data produced on the hosts.
