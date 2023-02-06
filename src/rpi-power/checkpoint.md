# Checkpoint

## Attach the LED and Resistor to the Pi Hat
[TODO: REMOVE THIS CHAPTER IF NO CHECKPOINTS]

Solder the 680 Ohm resistor and your LED to the Pi Hat as shown in the image.

```{tip}
The value of the resistor can be modified to adjust the brightness of the LED at full power. If you have additional resistors, you can modify this resistance by using a resistor with a smaller resistance, or by adding resistors in parallel later on. A helpful thread for understanding why this resistance should work is found [here](https://electronics.stackexchange.com/questions/378129/can-i-use-blue-green-leds-as-mcu-state-indicators-on-3-3-v-power).
```

```{attention}
The direction of the resistor does not matter, but the direction of the LED **does matter.** Be sure to place the cathode (shorter end) into the GND rail.
```

<figure>  
   <figcaption>Extra resistor wire snipped</figcaption>
   <img style='width:216px' src="photos/pihat-with-led.png"/>
</figure>


You've just finished the LED circuit! In a future lesson, you will learn how to send electricity through GPIO pin #6 to the LED and resistor, and then back to ground.