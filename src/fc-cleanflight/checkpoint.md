# Checkpoint


## Check the ESC ordering

Ensure the PWM wires are connected to the correct pins on the flight controller. Do this by following the PWM wires from the flight controller back to which motor the ESC is connected to. Make sure that this matches up with the image below.


<figure>
    <figcaption>Motors Diagram</figcaption>
    <img src="photos/correct_motors_diagram.jpg" width="200"/>
</figure>  

## Check the motor attachment

Make sure the arrows on the motors match up with the diagram above. It is important that the correct motors are in the correct spot because the motor bolts are threaded so that the propeller will not loosen the nut and fly off the drone.

## Check the motor direction

Make sure the motors are spinning in the correct direction. To do this, connect your flight controller to cleanflight with the **propellers off** and the battery plugged in, and spin up each motor to make sure it is spinning in the same direction as the arrow on the motor, which is the same direction as shown in the image above. It helps to put a small piece of tape on the side of the motor to know which way it is spinning.

```{figure} ../_images/fc-cleanflight/motors_spin_direction.png

Motors correct spin direction
```