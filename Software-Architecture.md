The design of FORT strictly separates the climate control from the vision in hardware and software. This improves the stability of the setup and facilitates the maintenance. On the highest level, **zeus** controls the climate and **leto** the vision/tracking.

# Tracking
The following chart explains the tracking software components.

<img alt="Tracking network" src="https://github.com/formicidae-tracker/documentation/raw/master/images/sw_structure_vision.png" width="400" />

> Grey boxes represent components developed in the course of the FORT project, white boxes represent external components.

**leto** implements the tracking user interface. It deals with the network communication between master and slaves, and configures the lower level **artemis** instances. *.leto* files are used to configure a tracking experiment. TODO describe components of leto.

**artemis** implements to computer vision functionality that detects tags and extracts their ID, position and orientation. It builds on the **apriltag**, **OpenCV**, **hermes** and **protobuf** libraries.

**hermes** implements low level data exchange of the tracking data, both for network data exchange and for saving the tracking data on file systems. It uses the google **protobuf** framework for serialization. TODO explain hermes library to be used by setup PCs to retrieve data in real time.

# Climate
The following chart explains the climate software and firmware components.

<img alt="Tracking network" src="https://github.com/formicidae-tracker/documentation/raw/master/images/swfw_structure_climate.png" width="300" />

> Grey boxes represent components developed in the course of the FORT project, white boxes represent external components. Green shadowed boxes represent firmware. For firmware description, refer to the [[Electronic Architecture|Electronic-Architecture]] page

**zeus** is the top level component that orchestrates the climate control system. A *.season* file allows to program climate states and transitions such as day and night. The zeus host application (shown on top of the figure) loads the configuration and initiates the climate control by providing a climate set-point to the zeus board. **zeus-calibrator** (not shown) is a helper program on the host to infer climate sensor offsets on the board. To use it, at least one additional **anemoi** board must be connected to the I2C bus (see below).

**libarke** implements the climate specific communication protocol, that builds on **cansocket** in order to transmit and receive messages via the **slcan0** CAN bus adapter.
