# Description

--- here a future tikz graph showing all the electronics ---

--- here a nicely written overall description of the electronics functionallities ---

# Electronic Buses and Power Rails

* Common Electronic Power Bus: 12V DC, max 5A.
* Illumination Power Bus: 36V DC max 1.65A
* CAN Bus: CAN version 2A running the [libarke protocol](https://github.com/formicidae-tracker/libarke.git) 
* Helios Trigger: Open Collector TTL Input for triggering the illumination system with the camera shutter

# Electronic boards description

## Zeus: climate control board

[[Technical Description | Zeus Datasheet ]]

Zeus reads the humidity and the temperature in the box via the Anemoi board over a I2C bus. It then runs a PID controller for each of these physical grandeur, and control them using:
 * Two extraction fans
 * A resistive heater (Notus)
 * The Celaeno humidifier

It runs sevral security euristic to ensure that the climate would be as safe possible even if there are other system under a break down.

## Celaeno: humidifier board

[[Technical Description | Celaeno Datasheet ]]

The Celaeno humidifier is used to raise the humidity in the boxe and help maintain a low temperature. Has a failure of this component can lead to a harmful climate for the ants, he also responsible to raise alarm to prevent any failure, such as an empty water tank.

## Arke: Isolated RS232 interface

[[Technical Description | Arke Datasheet ]]

Arke is a RS232 - CAN interface. The legacy RS232 port has been chosen over a more modern USB connection, has the system does not require so much bandwidth, but should be able to work over extended period of time undisturbed which is harder to guarantee with a managed port such as USB.

## Helios: Illumination System

* [[Technical Description of master board | Helios Master Datasheet ]]
* [[Technical Description of module | Helios Module Datasheet ]]

The Helios sub system is a powerful Infrared synchronised stroboscope, with a static illumination part.

## Anemoi: 

[[ Technical Description | Anemoi Datasheet ]]

The Anemoi board is used to install various type of sensor iver an I2C bus that would be read by the Zeus board.

## Prometheus : Power Distribution

A simple PCB with online LED used to distribute the power to all boards in the system.

## Notus: resistive heater

A PCB to mount on a 120mm PC Fan Power resistor to deliver up to 43 W of heating power. This PCB is simple enough to only says, do not touch heat when powered on, it burns.

# ECAD data:

All ECAD data can be found in the [hardware repository] (https://github.com/formicidae-tracker/hardware.git).

