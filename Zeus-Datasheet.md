# Zeus: Climate Control Board

The Zeus board is responsible for the climate monitoring and control:

* Continuously reads climate data and reports the temperature and humidity periodically (every 500 ms) over the CAN bus.
* Once a target climate operating point is set, it controls the **Notus** heater, the humidifier and the two exhaust fans to reach the desired climate.
* Sends various warnings and alerts over the CAN bus
  * Sends a warning when on for more than 5 seconds, without receiving a target climate operation point
  * Sends an alert when failing to reach a target climate operation point. This can happen for example when turning the exhaust fan at full power over an extended period of time.

## Connections:

* J1-J2: CAN Bus daisy chain.
* J3: 7V-25V Power input.
* J4: AVR 6 pin ICSP (only used for firmware upgrade)
* J5-J6, J10-J11: 4 Wire PC Fan Header 1 to 4
  * Fan 1: **Notus** Heater Fan
  * Fan 2: Box Extraction Fan Left
  * Fan 3: Box Extraction Fan Right
  * Fan 4: Unused
* J7: I2C sensor bus. At the moment, only anS **Anemoi** Board populated with a single humidity + temperature sensor is used.
* J8-J9: **Notus** heater connector.

## Security layer:

Upon certain exceptional conditions, the board will run in fail mode. In this mode, the PID control for the climate is disabled, the exhaust fans are turned on at full power, and the humidificator is off. This is to reach the lowest possible temperature (avoid overheating and very low humidity) without condensation (therefore the humidificator is off).

The conditions that trigger a fail mode are:

* No target climate point is specified after 5 seconds after a reset or power up.
* If for any reason the climate data is not readable during a period of more than a few seconds (humidity & temperature sensor failure).
