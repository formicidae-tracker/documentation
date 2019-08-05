# Arke: Isolated RS232 - Can Interface

Arke is an 3kV Isolated RS232 - CAN Interface. It implements the [CAN232](http://www.can232.com/docs/can232_v3.pdf) ASCII protocol which is supported by many OSes, including linux.

## LED indicators:

* **Green:** Ready. The RS232 input buffer is empty and thus ready to transmit and receive.
* **Orange:** Data. The CAN buffer is not empty, i.e. the device is receiving or transmitting a CAN Frame. Normal situation.
* **Blinking:** Error. Please notice that when a CAN Frame is not acknowledged, this will trigger an exceptional condition. Press the reset button to clear the error.

## Connections:

* J1: 7V-25V Power input.
* J2 : RS232 DB9 DCE connector
* J4: AVR 6 pin ICSP connector (for firmware upgrade)
* J3,J5 : CAN Daisy chain connector.
