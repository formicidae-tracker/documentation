# Zeus: Climate Control Board

The Zeus Board is responsible for the climate monitoring and control:

* It continuously read climate and report the temperature and humidity periodically (every 500 ms) over the CAN bus.
* Once a target point sets, it controls the Notus Heater the humidifier and the two exhaust fans to reach the desired climate.
* Sends various warnings and alert over the CAN Bus
  ** Sends a warning when powered one for more than 5 seconds buty did not received a target climate point
  ** Sends an alert when trying to reach a target point, but is unable to do so. For example when turning the exhaust fan at full power over an extended period of time 

## Connections:

* J1-J2: CAN Bus daisy chain.
* J3: 7V-25V Power input.
* J4: AVR 6 pin ICSP (only used for firmware upgrade)
* J5-J6, J10-J11: 4 Wire PC Fan Header 1 to 4
  * Fan 1: Notus Heater Fan
  * Fan 2: Box Extraction Fan Left
  * Fan 3: Box Extraction Fan Right
  * Fan 4: Unused
* J7: I2C sensor bus. At the moment, only an Anemoi Board populated with a single humidity + temeprature sensor is used.
* J8-J9: Notus Heating resistance connector.

## Security layer:

Upon certain exceptional conditions, the board will run in fail mode. In this mode, the PID control for climate is disabled, the exhaust fan are turned on at full power, and the humidificator is turned off. This in order to reach the lowest temeprature and not building up condensation in the box by letting the humidificator on.

The conditions that triggers a fail mode are:

* If no target climate point were given after 5 second after a reset or power up.
* If for any reason the climate data is not readable over a period of more than a few seconds (humidity & temperature sensor failure).


