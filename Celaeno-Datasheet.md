# Celaeno



## Operation:

If the water tanked is fully filled, when powered up the green LED will pulse slowly. Using the hermes protocol, any device on the bus can activate the humidificator, with a value between 1 and 255. The higher the value the faster the fan will spin. After a ramp up time the humidificator will turn on the piezo transducer, producing mist. This mist is then propelled to the ant box using the fan. When turned off, the piezo is immediatly turned off, but the fan will continue to spin for a few seconds. This avoids that condensation builds up on the fan, damaging it and making the humidifier fails.

When the water level will become low, the orange LED will constantly turn on, and the board will send an alarm signal repetivly over the CAN bus. When critical level is reached, the mist production is forced off, the orange LED will blink, and an alarm signal will alos repetively be emitted on the CAN bus. The humidifier

## Connections:

* J1-J2 : CAN Bus Daisy chain
* J3: Power Input 7V-25V
* J4: AVR ICSP 6 Wire programmer. Only used to update firmware
* J5-J6: 4-Wire PC Fan Header Fan 1 & 2 . Under Current Firmare only Fan 1 (J5) is used 
* J8-J9: Float Level Sensor. J8: Warning Level, J9: Critical Level.
* J7-J10: Relay In/Out for Piezo Transducer (Mist production). One side is plugged to the piezo transformer and the other to the piezo transducer.


## Changelog:

* Revision B: Adds TVS Diode on Fan Output to protect the EMC2302
* Revision A: Original Design