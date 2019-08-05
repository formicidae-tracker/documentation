# Celaeno

## Operation:

When the board is powered up and the water tanked is fully filled, the green LED pulses slowly. Using the **hermes** protocol, any device on the bus can activate the humidificator, with a value between 1 and 255. The higher this value, the faster the fan will spin. After a ramp-up time, the humidificator will turn on the Piezo transducer to producing mist which is then propelled to the ant box using the fan. When switched off, the Piezo is immediately shut down, but the fan continues to spin for a few seconds. This avoids that condensation builds up on the fan, that will eventually damage it.

When the water level will becomes low, the orange LED is constantly on and the board repetitively sends an alarm over the CAN bus. When the critical level is reached, the mist production is shut down, the orange LED blinks and an alarm signal is sent repetitively over the CAN bus.

## Connections:

* J1-J2 : CAN Bus Daisy chain
* J3: Power Input 7V-25V
* J4: AVR ICSP 6 Wire programmer. Only used to update firmware
* J5-J6: 4-Wire PC Fan Header Fan 1 & 2 . Under Current Firmware only Fan 1 (J5) is used
* J8-J9: Float Level Sensor. J8: Warning Level, J9: Critical Level.
* J7-J10: Relay In/Out for Piezo Transducer (Mist production). One side is plugged to the piezo transformer and the other to the Piezo transducer.


## Changelog:

* Revision B: Adds TVS Diode on Fan Output to protect the EMC2302
* Revision A: Original Design
