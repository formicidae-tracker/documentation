# Overview

The electronic components are the backbone of the FORT. These are
organized with a modular architecture, were each electronic board
endorses a few roles only, such has implementing the climate control
loop, managing illumination, managing the humidification process...

<img alt="Fort overview" src="https://github.com/formicidae-tracker/documentation/raw/draft-matthias/images/FORTplan.png"/>
> Schematic overview of the FORT setup with photo of one instance at UNIL. The tracking host computer is not show on the photo.

The following schematic diagram shows the electronic components and connections of the FORT.

![Electronic Architecture](https://github.com/formicidae-tracker/documentation/raw/master/tikz/electronic-architecture.png)
> In order to lighten this diagram, the 12V Power Rails distribution from **Prometheus** to **Arke**, **Zeus**, **Helios** and **Celaeno** are ommitted.


In order to firewall any electrical issue on the system, there are two
galvanic isolation barriers that isolate the electronic components in
three sets:

* General Electronic with 12V Power rails
* Power Illumination Electronic over 36V rails
* Machine Vision & Computing Electronics, powered from the computer
  ATX power supply.

# Electronic Buses and Power Rails


The system features multiples power rails and communication bus. The main elements are :

* a common electronic rails that power up most of the electronics. Its
  power supply uses a 12V DC 60W powersupply, over a 5.5mm Outer
  Diameter (O.D.)  2.5mm Inner Diameter (I.D.) Barrel Jack. Excepted
  **Prometheus**, all the electronic boards uses a Molex 5557
  connector to receive the power as depicted below.  
<img alt="12V Power Connector" src="https://github.com/formicidae-tracker/documentation/raw/master/images/12V.png" width="250" />

* an illumination rails, for all the illumination equipment. Its power
  supply uses a 36V DC 60W with a 5.5mm O.D. 2.1 mm I.D.

> __IMPORTANT: The choice of a 36V smaller barrel jack (2.1mm I.D.)
>  compared to the 12V (2.5mm I.D.) is motivated to avoid any connection
>  by mistake of the 36V Power Supply over the 12V rails. Physically forcing
>  the 36V plug in the 12V receptacle of **Prometheus** would results in
>  instantaneous and irreversible destruction of all the 12V powered
>  electronics.__


* a CAN Bus: CAN version 2A running the [libarke
  protocol](https://github.com/formicidae-tracker/libarke.git) that
  handles most of the inter-device electronic communication.
  The connector used for these cables is illustrated below:
<img alt="CAN Connector" src="https://github.com/formicidae-tracker/documentation/raw/master/images/CAN.png" width="250" />

* a CoaXPress CXP-6 4x Link: that interfaces the computer and the camera via a
  framegrabber.
* an illumination trigger cable that permits the synchronisation
  between the camera and the infrared lighting. It uses an open
  collector TTL Output of the framegrabber. The connector for this
  cable is illustrated below:
<img alt="CAN Connector" src="https://github.com/formicidae-tracker/documentation/raw/master/images/trigger.png" width="250" />

* a Helios daisy chain that dispatches an isolated 6V and 36V power rails, and
  balanced trigger and data signal. These cables uses the following connector:
<img alt="CAN Connector" src="https://github.com/formicidae-tracker/documentation/raw/master/images/helios.png" width="250" />


* A RS232 interface that connects the computer to the CAN Bus. It uses a DB9 DCE Cable. The Arke End is connected to a DB-9 femelle connector:
<img alt="CAN Connector" src="https://github.com/formicidae-tracker/documentation/raw/master/images/RS232.png" width="250" />





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
