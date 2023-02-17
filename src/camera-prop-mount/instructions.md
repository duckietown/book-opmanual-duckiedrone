# Instructions

## Attach the standoffs to the bottom frame
Attach the 4 long nylon white standoffs to the bottom of the frame by screwing them with an M2 nylon screw on the back of the bottom frame, as shown in the image.

```{figure} ../_images/camera-mounting-hw/standoffs_in_frame.png

Nylon standoffs mounted on bottom frame
```

## Secure the battery to the frame
Place the battery in between the nylon standoffs and secure it to the frame by using zip ties and a Velcro strap.

```{attention} 
Make sure to secure the battery tightly to the frame to avoid it moving during flight.
```

```{tip}
You can use the holes in the rear part of the frame (towards the PDB) to attach the battery cables using a zip ties. 

This minimizes the sideways wobbling of the battery.
```

```{figure} ../_images/camera-mounting-hw/battery_secured.png

Battery secured to the frame using zip ties and velcro strap
```
## Attach the TOF sensor

```{important}
There's a tiny piece of yellow tape on the black tab, make sure to remove it before attaching it to the drone
```

1. Place the TOF sensor on the left hole, making sure to align the small black plastic tab with it.

1. Using one M3 bolt and nut, screw the TOF sensor to the frame.

## Attach the Pi Camera to the drone frame
The Pi Camera has to be secured to the frame. 

```{attention}
The Pi Camera has tape on the back of the black lens assembly that has to be fixed to the PCB **before** mounting it on the frame
```

1. Peel off the tape on the back side of the lens assembly of the Pi Camera and attach it to the PCB

1. Make sure the flex connector (called *FFC* ) from the lens assembly is attached to its connector.

    ```{figure} ../_images/camera-mounting-hw/camera_connector.png

    Camera with lens assembly attached and connected
    ```
1. Screw the Pi Camera to the right hole in the front part of the drone using the small metal bolts and nuts. Attach on top, so that the camera faces downward and the FFC goes towards the battery drone.

    ```{figure} ../_images/camera-mounting-hw/camera_tof_sensor_attached.png

    Camera (and TOF sensor) attached to the front of the frame

## Mount the top frame
1. Identify the small black rectangular laser cut piece of the frame.

1. Attach the large nylon spacers through the small screw holes using the M2 nylon screws.

    ```{important}
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

1.  Identify the 4 holes on the top frame and place nylon spacers on each
    ```{image} ../_images/camera-mounting-hw/top_frame_spacers.png
    ```

1.  Place the Raspberry Pi on top, taking care not to move the spacers

1.  Use 4 small zip ties to secure the Raspberry Pi in place
    ```{image} ../_images/camera-mounting-hw/raspberry_pi_attached.png
    ```

## Connect the camera and attach the Pi Hat
You will now connect the camera to the Raspberry Pi and attach the Pi Hat. 

```{important}
The camera connector cable (called *FFC*) has to go through the opening of the Pi Hat *before* this is attached to the Raspberry Pi in order to be able to connect it to the Raspberry Pi.
```

```{attention} 
The flex cable has to be twisted in order to have the correct orientation **before being inserted** through the opening on the Pi Hat
```

1.  Feed the *FFC* cable through the opening of the Pi Hat as shown in the picture. 
    ```{note}
    Make sure that the Pi Hat is oriented with the pins facing up and on the same side as the pins of the Raspberry Pi, and that the blue tape is facing up as in the figure.
    ```

    ```{figure} ../_images/camera-mounting-hw/ffc_through_hat.png

    Pi Camera flex cable going through the Pi Hat
    ```

1.  Attach the cable to the *FFC* connector making sure to have the blue tape on the cable facing the black plastic tab on the connector.  
    ```{tip} 
    Watch this video to understand how to attach the connector properly
    <iframe width="560" height="315" src="https://www.youtube.com/embed/VzYGDq0D1mw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    ```

1.  Attach the Pi Hat to the GPIO pins of the Raspberry Pi being careful when handling the flexible camera cable.

    ```{figure} ../_images/camera-mounting-hw/pi_hat_connected.png

    Pi Hat connected to the Raspberry Pi with the camera cable routed through its opening
    ```

## Attach UBEC
Use a piece of foam double sided tape to attach the UBEC to the top of the USB ports of the Raspberry Pi as shown.

```{figure} ../_images/camera-mounting-hw/ubec_attached.png

UBEC attached to the Raspberry Pi USB ports
```

## Connect sensors and UBEC

1. Connect the UBEC to the pins soldered on the `5V` and `GND` rails
    ```{danger}
    Be careful to not connect the UBEC to the WiFi mode selection pins as doing so will damage your Raspberry Pi
    ```

1.  Attach the soldered TOF cable from the Pi Hat to the TOF sensor.
    ```{image} ../_images/camera-mounting-hw/tof_sensor_attached_cable.png
    :width: 400px
    ```

1.  Connect the Flight Controller USB cable to one of the USB ports on the Raspberry Pi

```{note}
If you have the `OSD` version of the Flight Controller, you can use a piece of double sided foam tape to attach the USB connector board to the frame, right beneath the PDB board.

    ```{figure} ../_images/camera-mounting-hw/OSD_usb_board.png

    USB board attached to the frame (`OSD` Flight Controller)
    ```

## Fix cables to the frame
Make sure to attach all dangling cables using zip ties to the frame, such that no wires can hit the propellers.

```{figure} ../_images/camera-mounting-hw/pwm_wires_fixed.png

PWM wires fixed to the bottom of the frame
```
