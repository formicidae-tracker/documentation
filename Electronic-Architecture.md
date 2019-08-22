# Description

The electronic components are the backbone of the FORT. These are
organized with a modular architecture, were each electronic board
endorses a few role only, such has implementing the climate control
loop, managing illumination, managing the humidifcation process...

![Electronic Architecture](/tikz/electronic-architecture.png)

The backbone of inter-device communication is done using a CAN bus. In
order to firewall any electrical issue on the system, there are two
galvanic isolation barrier that isolate the elements in three set:

* General Electronic with 12V Power rails
* Power Illumination Electronic over 36V rails
* Machine Vision & Computing Electronics, powered from the computer
  ATX power supply.

# Electronic Buses and Power Rails

* Common Electronic Power Bus: 12V DC, max 5A.
* Illumination Power Bus: 36V DC max 1.65A
* Piezotransducer Alimentation: 24V AC
* CAN Bus: CAN version 2A running the [libarke
  protocol](https://github.com/formicidae-tracker/libarke.git)
* RS232 Serial cable, connect all the electronics to the computer
* CoaXPress CXP-6: interfaces computer to the camera via a
  framegrabber.
* Helios Trigger: open collector TTL Input for triggering the
  illumination system with the camera shutter
* Helios Daisy Chain: vable dispatching a 6V and a 36V power rail, and
  isolated trigger and data signal.


# Electronic Boards Description

## Zeus: Climate Control Board

[[Technical Description | Zeus Datasheet ]]

**Zeus** reads the humidity and the temperature in the box via the
**Anemoi** board over a I2C bus. It then runs a PID controller for
each of these physical grandeur, and control them using:
 * Two extraction fans
 * A resistive heater (**Notus**)
 * The **Celaeno** humidifier

It runs sevral security heuristic to ensure that the climate would be
as safe possible even if there are other system under a break down.

## Celaeno: Humidifier Board

[[Technical Description | Celaeno Datasheet ]]

The **Celaeno** humidifier is used to raise the humidity in the box
and help maintain a low temperature. Since a failure of this component
can lead to a harmful climate for the ants, it also responsible to
raise alarms to prevent any failure, e.g. due to an empty water tank.

## Arke: Isolated RS232 Interface

[[Technical Description | Arke Datasheet ]]

**Arke** is a RS232 - CAN interface. The legacy RS232 port has been
chosen over a more modern USB connection, because the system does not
require much bandwidth, but should be able to work over extended
period of time without disturbance. This is harder to guarantee with a
managed port, such as USB.

## Helios: Illumination System

The **Helios** sub-system is a powerful synchronised infrared
stroboscope, with a static illumination part for visible light. The
user can program the visible light to simulate a circadian cycle.

* [[Technical Description of master board | Helios Master Datasheet ]]
* [[Technical Description of module | Helios Module Datasheet ]]

## Anemoi: Sensor Terminal

The **Anemoi** board is used to install various types of sensors whose
values are read by the **Zeus** board via an I2C bus.

[[ Technical Description | Anemoi Datasheet ]]

## Prometheus : Power Distribution

A simple PCB to distribute the power to all boards in the system. It
has an LED *online* status indicator.

## Notus: Resistive Heater

A PCB to mount on a 120mm PC Fan Power resistor to deliver up to 43 W
of heating power. This PCB is simple enough to only says, do not touch
heat when powered on, it burns.

# ECAD data:

All ECAD data can be found in the [hardware repository]
(https://github.com/formicidae-tracker/hardware.git).
