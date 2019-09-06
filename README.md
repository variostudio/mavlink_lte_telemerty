# Passing MAVLINK telemetry via LTE

This tutorial is about connecting MavLink based flight controller to GroundStation software via LTE for long-range vehicles

## Parts and materials
The required parts for this project:
* MavLink-based FC. I'd used Matek Wing F405 with Ardupilot software
* Raspberry PI
* 5v to 3.3v voltage divider
* Wires etc.

```SH
#!/bin/bash

socat TCP-LISTEN:4161,fork,reuseaddr FILE:/dev/ttyAMA0,b57600,raw
```

