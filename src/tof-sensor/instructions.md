# Instructions

1. Strip about 5 mm off of the newly-exposed ends of the ToF sensor wire
1. Twist and Tin the ToF sensor wires. 
    ```{attention} Do not put too much solder, as the wires must fit through the holes in the Raspberry Pi Hat
    ```
1. Solder the ToF sensor wires to the Raspberry Pi Hat following [the figure](soldered-tof-cable) below:
    * insert a wire into the correct hole in the front of the Raspberry Pi Hat. 
    * Solder the red wire to the `+3V` rail
    * Solder the black wire to the `GND` rail
    * Solder the yellow wire to `SCL` hole
    * Solder the blue wire to `SDA` hole

1. Trim the excess cable on the back side of the Pi Hat (where you just soldered it)

```{figure} ../_images/tof-sensor/soldered-tof-cable.jpg
:name: soldered-tof-cable

Soldered TOF sensor cable
```
