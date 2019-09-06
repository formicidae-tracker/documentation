Testing and taking a setup into operation usually involves some debugging. This page describes some tools to make sure that the setup is functional.

# Climate

* Create a climate file (.season). One is in root on fort setup. scp it to the master.

```bash
scp seasonfile.season fort-user@master-name.local:
```

* ssh fort-user@runestone.local pw:123456
or via remmina
`temnothorax.season run`
for the climate data live feed on any PC connected to the local network (__Iron throne__), go to a browser (chrome preferred) and:
`castle-black.local:3000`

Command line tools that can be used on any master (connection via VNC, e.g. remmina):

# Light modules

Before unplugging the light board, always unplug the main power for the arke board.

# Camera

* To see the camera live feed
```bash
artemis -d
```
Arrows and the mouse can be used to pan and zoom the image

# Hardware connectivity

* To see the can bus communication in real time:
```bash
arkedump slcan0
```

* To restart the can bus service:
```bash
sudo systemctl restart serial-slcand@ -> autocomplete
```
