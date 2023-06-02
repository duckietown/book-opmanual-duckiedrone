# Instructions

## Attach the standoffs to the bottom frame

Attach the 4 long nylon white standoffs to the bottom of the frame by screwing them with M2 nylon screws on the back of the bottom frame, as shown in the image.

```{figure} ../_images/camera-mounting-hw/standoffs_in_frame.png

Nylon standoffs mounted on bottom frame
```

## Secure the battery to the frame

Place the battery in between the nylon standoffs and secure it to the frame by using one zip tie and a Velcro strap.

```{tip}
To allow the battery to be hot-swapped easily after a flight it is suggested to attach the velcro strap such that you can open it from the bottom side of the drone.
```

```{attention}
Make sure to secure the battery tightly to the frame to avoid it moving during flight.
```

```{tip}
You can use the holes in the rear part of the frame (towards the PDB) to attach the battery cables using a zip ties. 

Keep this zip tie loose to allow swapping out the battery quickly.

This minimizes the sideways wobbling of the battery.
```

```{figure} ../_images/camera-mounting-hw/battery_secured.png

Battery secured to the frame using zip ties and velcro strap
```

## Attach the ToF sensor

```{attention}
There's a tiny piece of yellow tape on the black tab, make sure to remove it before attaching it to the drone
```

1. Place the ToF sensor on the smaller left hole, making sure to align it so that the small black chip is looking down **through** the hole.

1. Using one M3 nylon bolt and nut, screw the ToF sensor to the frame.

## Attach the Raspberry Pi Camera to the drone frame

The Raspberry Pi Camera has to be secured to the frame.

```{attention}
The Raspberry Pi Camera has tape on the back of the black lens assembly that has to be fixed to the PCB **before** mounting it on the frame
```

1. Peel off the tape on the back side of the lens assembly of the Raspberry Pi Camera and attach it to the PCB

1. Make sure the flex connector (called *FFC*) from the lens assembly is attached to its connector.

    ```{figure} ../_images/camera-mounting-hw/camera_connector.png

    Camera with lens assembly attached and connected
    ```
1. Screw the Raspberry Pi Camera to the right hole in the front part of the drone using the small nylon bolts and nuts. Attach on top, so that the camera faces downward and the FFC goes towards the drone's battery.

    ```{figure} ../_images/camera-mounting-hw/camera_tof_sensor_attached.png

    Camera (and ToF sensor) attached to the front of the frame
    ```

```{warning}
Do not use the metal M2 screws as they might short the PCB.

Only use them if you have an old hardware revision, see Troubleshooting if you have power issues.
```

## Mount the top frame

1. Identify the smaller black rectangular laser cut piece of the frame.

1. Attach the large nylon spacers through the small screw holes using four M2 nylon screws.

    ```{attention}
    Make sure the upper frame is oriented in the correct direction, as shown in the figure.

    There is a larger rectangular opening in it that shall be oriented towards the back of the drone.
    ```

    ```{figure} ../_images/camera-mounting-hw/top_frame_mounted.jpg

    Top frame mounted on the standoffs (ignore the bolts protruding)
    ```

    ```{tip}
    You might need to slightly squeeze the nylon standoffs together due to the battery being in between them. 

    This is okay, and it has also the benefit of further securing the battery to the frame
    ```

## Mount the Raspberry Pi

Now you are going to attach the Raspberry Pi to the top of the frame using zip ties.

1. Identify the 4 holes on the top frame and place nylon spacers on each

    ```{image} ../_images/camera-mounting-hw/top_frame_spacers.png
    ```

1. Place the Raspberry Pi on top, taking care not to move the spacers

1. Mount the Raspberry Pi on top using the 4 M2.5 nylon screws: insert them from the bottom and screw them in the short M2.5 spacers.

    ```{figure} ../_images/camera-mounting-hw/raspberry_pi_with_spacers.jpg
    :name: complete-raspberry-hat

    Raspberry Pi mounted on the upper frame (with Raspberry Pi Hat)
    ```

```{note}
Some old hardware revisions did not have enough M2.5 nylon screws. If this is the case you can use 4 small zip ties to secure the Raspberry Pi in place.
    ![](../_images/camera-mounting-hw/raspberry_pi_attached.png)
```

## Connect the camera and attach the Raspberry Pi Hat

You will now connect the camera to the Raspberry Pi and attach the Raspberry Pi Hat.

```{attention}
The camera connector cable (called *FFC*) has to go through the opening of the Raspberry Pi Hat *before* this is attached to the Raspberry Pi in order to be able to connect it to the Raspberry Pi.
```

1. Feed the *FFC* cable through the opening of the Raspberry Pi Hat as shown in the picture.

    ```{note}
    Make sure that the Raspberry Pi Hat is oriented with the pins facing up and on the same side as the pins of the Raspberry Pi, and that the blue tape is facing up as in the figure.
    ```

    ```{figure} ../_images/camera-mounting-hw/ffc_through_hat.png

    Raspberry Pi Camera flex cable going through the Raspberry Pi Hat
    ```

1. ```{figure} ../_images/camera-mounting-hw/attaching-camera-1.png
    :width: 500px

    Lift the camera connector plastic flap.
    ```

1. ```{figure} ../_images/camera-mounting-hw/attaching-camera-2.png
    :width: 500px

    Insert the camera cable in the connector with the blue side facing towards the Ethernet port and close the plastic flap.
    ```

    ```{seealso}
    Watch this video to understand how to attach the connector properly
    <iframe width="560" height="315" src="https://www.youtube.com/embed/VzYGDq0D1mw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    ```

1. Attach the Raspberry Pi Hat to the GPIO pins of the Raspberry Pi being careful when handling the flexible camera cable.

    ```{figure} ../_images/camera-mounting-hw/pi_hat_connected.png

    Raspberry Pi Hat connected to the Raspberry Raspberry Pi with the camera cable routed through its opening
    ```

## Attach the UBEC

Use a piece of foam double-sided tape to attach the UBEC to the top of the USB ports of the Raspberry Pi as shown.

```{figure} ../_images/camera-mounting-hw/ubec_attached.png

UBEC attached to the Raspberry Pi USB ports
```

## Connect sensors and UBEC

1. Connect the UBEC to the pins soldered on the `5V` and `GND` rails

    ```{danger}
    Be careful to not connect the UBEC to the WiFi mode selection pins as doing so will damage your Raspberry Pi
    ```

1. Attach the soldered ToF cable from the Raspberry Pi Hat to the ToF sensor.

    ```{image} ../_images/camera-mounting-hw/tof_sensor_attached_cable.png
    :width: 300px
    ```

1. Connect the Flight Controller USB cable to one of the USB ports on the Raspberry Pi

````{note}
If you have the `OSD` version of the Flight Controller, you can use a piece of double sided foam tape to attach the USB connector board to the frame, right beneath the PDB board.

```{figure} ../_images/camera-mounting-hw/OSD_usb_board.png
:width: 400px

USB board attached to the frame (`OSD` Flight Controller)
```

Angle it so that the USB connector doesn't protrude much, otherwise you might encounter clearance issues with the propellers.
````

## Fix cables to the frame

Make sure to attach all dangling cables using zip ties to the frame, such that no wires can hit the propellers.

```{attention}
Fix the cables to allow the drone to lie flat on the ground.
This is important to calibrate the Flight Controller.
```

```{figure} ../_images/camera-mounting-hw/pwm_wires_fixed.png
:width: 400px

PWM wires fixed to the bottom of the frame (zip tie in the center)
```

````{danger}
Make sure ESC-motor wires are ziptied down properly. If not, you risk having a short.

```{figure} ../_images/camera-mounting-hw/esc_cables_tied.jpg
:width: 400px

Properly tied ESCs cables
```

````

## Attach propellers

Attach the propellers to the drone so that it may fly: attach CW propellers to the CW motors, and CCW propellers to the CCW motors.

````{attention}
The propellers have small arrows on them in the center to indicate which type they are.

```{figure} ../_images/camera-mounting-hw/propellers_arrows.jpg

Arrows on the propellers indicating spin direction
```

````

```{tip}
The nuts for the motors that spin CCW tighten when turned CW, and the ones on the motors that spin CW tighten when turned CCW.
```

Use the 8 mm wrench to tighten the bolts down so that the bottom of the propeller is flat on the top of the motor.

```{warning}
Screw bolts down tightly, but not so tight that you could not remove the propellers if you had to.
```

```{figure} ../_images/camera-mounting-hw/propellers_attached.jpg

Propeller attached to the motors
```

## Battery Monitor

In your Duckiebox there is one item that we haven't used so far: the Battery Monitor.

```{note}
This is optional and not required for flight.
```

To use this safety device you are going to have to connect it to the 4-pins connector of the LiPo battery, when it is not charging:

1. Identify the row of pins at the bottom of the Battery Monitor.
1. Connect the 4-pins connector to the left-most pins, having the first pin connected to the black (`-`) wires of the connector.

    ```{figure} ../_images/camera-mounting-hw/battery_monitor_connector.png

    Battery connected to the Battery Monitor
    ```

    ```{warning}
    The battery monitor makes a **very loud** sound when it powers up.
    
    You can cover the speaker holes on the opposide side from the row of pins to protect your ears.
    ```

1. Secure the battery monitor to the chassis of the Duckiedrone.

    ````{note}
    Due to the length of the battery cable and the limited space on the frame there is not a great mounting spot.

    You should pick one making sure that:

    *   The Battery Monitor and battery wire do not interfere with the propellers.
    *   The Battery Monitor will not move during flight.

    ```{figure} ../_images/camera-mounting-hw/battery_monitor_location.png

    A possible location to attach the Battery Monitor
    ````

    ```{tip}
    You can use some double-sided tape to fix the battery monitor.
    ```
