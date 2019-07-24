# Arke: Isolated RS232 - Can Interface

Arke is an 3kV Isolated RS232 - CAN Interface. It implements the [CAN232](http://www.can232.com/docs/can232_v3.pdf) ASCII protocol which is supported by many OSes, including linux.

## LEDs:

* Ready (Green): When On, the RS232 input buffer is not filled (ready to transmit and receive
* Data (Orange):  When on the CAN buffer is not empty (receiving or transmitting a CAN Frame)
* Error (Blink under exceptionnal condition). PLease notice that when a CAN Frame is not acknowledge, this will trigger an exceptionnal condition. Press the reset button to clear the error.
 
## Connections:

* J1: 7V-25V Power input.
* J2 : RS232 DB9 DCE connector
* J4: AVR 6 pin ICSP connector (for firmware upgrade)
* J3,J5 : CAN Daisy chain connector.