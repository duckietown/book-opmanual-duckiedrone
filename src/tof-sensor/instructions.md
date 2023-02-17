# Instructions

1. Strip about 5mm off of the newly-exposed ends of the IR sensor wire
1. Twist and Tin the IR sensor wires. 
```{attention} Do not put too much solder, as the wires must fit through the holes in the Pi Hat
```
1. Solder the TOF Sensor Wires to the Pi Hat following [the figure](soldered-tof-cable) below:
    * insert a wire into the correct hole in the front of the Pi Hat. 
    * Solder the red IR Sensor Wire to the `3V` rail
    * Solder the black IR Sensor Wire to the `GND` rail
    * Solder the yellow IR Sensor Wire to `SCL` rail
    * Solder the blue IR Sensor Wire to `SDF` rail

1. Trim the excess cable on the back side of the Pi Hat (where you just soldered it)

```{figure} ../_images/tof-sensor/soldered-tof-cable.jpg
:name: soldered-tof-cable

Soldered TOF sensor cable
```
