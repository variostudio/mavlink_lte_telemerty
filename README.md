# Passing MAVLINK telemetry via LTE

This tutorial is about connecting MavLink based flight controller to GroundStation software via LTE for long-range vehicles

## Parts and materials
The required parts for this project:
* MavLink-based FC. I'd used Matek Wing F405 with Ardupilot software
* Raspberry PI
* 5v to 3.3v voltage divider
* Wires etc.

## Flight controller set up.
* Choose free UART on FC. It would be UART5 for this tutorial.
* Configure it as MavLink2, 57600 bps

## Wiring
* Connect Raspberry GPIO uart (pins 8, 10) via voltage divider to FC uart (T5, R5)
* Connect grounds

## Raspberry PI configuration
* Enable GPIO uart and disable using UART by console
* set up `socat` to Raspberry PI with `sudo apt-get install socat`
* Create script listed below:

```SH
#!/bin/bash

socat TCP-LISTEN:4161,fork,reuseaddr FILE:/dev/ttyAMA0,b57600,raw
```
This scripts maps UART ttyAMA0 to port 4161

## Ground Control Station setup
* Create connection in your GSC software:
** Type: TCP
** Port: 4161

## Connect it!
