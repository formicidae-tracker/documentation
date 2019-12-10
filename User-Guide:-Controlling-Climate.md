# Context and precautions

TLDR: Always:
 * Operate the system in a room maintained at a temperature 2 to 3°C below the minimal desired temperature
 * Always make sure the humidification is operating properly.

In order to ensure a sufficient image quality for computer vision processing, powerful infrared flashes are used in synchronization with the camera. The illumination system can consume in average up to 60W of power, that will be dissipated in the box. Therefore a sufficient cooling system should be used to keep the ant under a desired climate (between 22°C and 29°C depending on the species). Heat can easily build up in the isolated boxes, and put in danger the life of the ant colony.

To cool down the box, two effects are used:
* Intake of cooler air from the surrounding tracking room, that should be climate controlled and kept around 21°C.
* Increase of the humidity to 60% R.H - 70% R.H. For example, humidifying a dry air at 20°C and 20% R.H. to 60% R.H. will lower its temperature up to 13°C. Even if its counter intuitive, this effect could even be stronger than replacing the box air with the room air.

Therefore there is a strong coupling between the humidification and the temperature control in the box. It explains, why, having a humidifier failure over an extended period of time could lead to an harmful temperature for the ants.

If the climate of room in which the climate tracking system is operated is also really important. If left un-managed, a hot and wet weather, like a thunderstorm, may have catastrophic failure. Indeed the system will only had a few or even no humidity since the external air is already quite wet, and therefore will only rely on replacing the air to cool down the box.

The current version of fort have been tested to be able to only allow an increase of 2 to 3°C under a humidification failure when the illumination system is running at full power. Operating the system in a room, air conditioned to be at a temperature 2 to 3°C below the minimal desired temperature in a box ensures that this desired temperature can always be maintained, regardless of the local weather.

# Setting up

1. Ensure that all the electronic is correctly plugged. Plug everything excepted the main power.
2. Ensure that the humidifier is filled with de-ionized water.
3. Verify that the temperature and humidity sensor (anemoi board) is plugged to the climate control board (zeus)
4. Verify that the CAN bus daisy chain is set up properly
5. Verify that RS232 cable is plugged to Arke and the controlling computer.
6. Plug the electronic main power.
7. Run the zeus command on the master computer.
```bash
zeus -c my_desired_climate.season run
```
8. Verify on the Olympus gateway that the box climate is running.

Please refer to the [zeus](https://github.com/formicidae-tracker/zeus) to learn more about the zeus command, the season file format and its capabilities.
