# Checkpoint

## Checking the ESC communication with Flight Controller

- When you connect the drone to power, the ESCs should make a "`boop` `boop` `boop`" sound, followed by a "`beep` `BEEEEEP`" sound.

```{admonition} Joke
We are working on enabling a "`quack` `quack`" sound.
```

## Checking the ESC ordering

Ensure the PWM wires are connected to the correct pins on the flight controller. Do this by following the PWM wires from the flight controller back to which motor the ESC is connected to. Make sure that this matches up with the image below.


```{figure} ../_images/fc-cleanflight/motors_numbering.png
:align: center

Motors numbering
``` 
## Checking the motor direction

```{danger}

Always take off propellers when testing the motors.

```

Make sure the motors are spinning in the correct direction. To do this, connect your Flight Controller to Cleanflight with the **propellers off** and the battery plugged in, and spin up each motor to make sure it is spinning in the same direction as the direction shown in the image below.

```{tip}
It helps to put a small piece of tape on the side of the motor to know which way it is spinning.
```

```{figure} ../_images/fc-cleanflight/motors_spin_direction.png

Motors correct spin direction
```