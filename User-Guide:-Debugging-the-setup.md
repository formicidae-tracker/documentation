Testing and taking a setup into operation usually involves some debugging. This page describes some tools to make sure that the setup is functional.

# Climate

* Create a climate file (.season). One is in root on fort setup. scp it to the master.

```bash
scp seasonfile.season fort-user@master-name.local:
```

* ssh fort-user@runestone.local pw:123456
or via remmina
`temnothorax.season run`
for the climate data live feed on any PC connected to the local network, use a web browser (chrome preferred) and and connect to the gateway address.

Command line tools that can be used on any master (connection via VNC, e.g. remmina):

# Light modules

Before unplugging the light board, always unplug the main power for the arke board.

# Camera

* To see the camera live feed
```bash
leto-cli
```
Using the leto-client without providing an experiment name starts the test mode.
This allows to get live images with overlayed tag detection to adjust the optics for an optimal result. A watermark "test-mode" on the video indicates that no data is currently saved.

# Hardware connectivity

* To see the can bus communication in real time:
```bash
arkedump slcan0
```

* To restart the can bus service:
```bash
sudo systemctl restart serial-slcand@ -> autocomplete
```
