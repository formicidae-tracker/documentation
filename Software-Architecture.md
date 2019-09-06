The design of FORT strictly separates the climate from the visual functionality in hardware and software. This improves the stability of the setup and facilitates the maintenance. On the highest level, **zeus** controls the climate and **leto** the tracking.

# Tracking
The following chart explains the tracking software components. Grey boxes represent components developed in the course of FORT, white boxes represent external components.

---> Chart here

**leto** implements the tracking user interface. It deals with the network communication between master and slaves, and configures the lower level **artemis** instances. *.leto* files are used to configure a tracking experiment. TODO describe components of leto.

**artemis** implements to computer vision functionality that detects tags and extracts their ID, position and orientation. It builds on the **apriltag**, **OpenCV**, **hermes** and **protobuf** libraries.

**hermes** is a library that implements the communication protocol for tracking data. It uses the google **protobuf** framework for serialization. TODO explain hermes library to be used by setup PCs to retrieve data in real time.

# Climate
The following chart explains the climate software and firmware components.

---> Chart here
