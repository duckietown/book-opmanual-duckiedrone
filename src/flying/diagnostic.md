# Common issues


```{trouble}
The red light on the Raspberry Pi :

*   is blinking
*   does not turn on

---

The Raspberry Pi is not receiving enough power. 

- Check that the voltage coming out of the UBEC is a constant 5V

- Make sure that the Raspberry Pi Hat is attached to the Raspberry Pi all the way (there is no gap between the GPIO pins and the Raspberry Pi Hat pin header).

- Make sure that the `OUTPUT` side of the UBEC is attached to the Raspberry Pi Hat, and the `INPUT` side is soldered to the PDB

- Make sure that there is not a short between the power and ground rails on the Raspberry Pi Hat.

- Make sure there are no stray wire hairs that are shorting out the `5V` and the `GND` rails on the Raspberry Pi Hat

```

```{trouble}
The flight code does not start

---

Make sure you are running the start script in the correct directory: `~/ws/src/pidrone_pkg`, **inside** the container.
```

```{trouble}
The `roscore` screen does not startup.
---
Quit the screen by typing the tick (\`) followed by colon (`:`) and the type the word `quit` and press enter. You will not see the tick and colon typing, but you will see "quit" as you type at the bottom of the screen. 

Check if there re multiple screens running by typing `screen -ls` in the terminal.

You will need to quit each socket found so that only one screen session is running. To do so:

For each socket found, there is a name that looks like `2503.pts-0.duckiesky-drone`. The four numbers at the beginning, `2503` are the session id. Run this command for each session id:

`screen -S [session id] -X quit`

For example, for this session it would be `screen -S 2503 -X quit`
Be sure that the 'S' and 'X' are capitalized.
```

```{trouble}
The flight controller node does not start correctly.

---

The last line printed out should be `/pidrone/battery`.

If the last line printed out says that the USB is not plugged in:

- make sure that the USB is plugged into any one of the four USB ports on the Pi.

- make sure that the micro USB is plugged into the flight controller.

- rerun  `python flight_controller_node.py`.

If you get the error again:

- make sure that the flight controller is lighting up in some way. If it is not, the micro USB port on the flight controller may be broken.

- try wiggling the micro USB end or using a different USB port on the Pi. If the flight controller never lights up, it may need to be replaced.
```

```{trouble} 

The PID controller node is not running.

---

The last line printed out should state `PID Controller Started`.
If this is not the case:

- Try quitting the script with `ctrl-c` and rerunning it
```

```{trouble}
The state estimator is not running.

---
In the state estimator screen the last line printed out should state `Starting filter`.

- make sure the flight controller node is running, as data is needed from the imu to start the filter.

- continue with the checks to make sure the other sensors are working, then try rerunning this script
```

```{trouble}
The vision node is not running.
---

The last line printed out in the vision node screen should state `Vision started`.

If the last few lines print: `out of resources other than memory`, then the issue is the physical connection from the camera to the Raspberry Pi.

- make sure that the sunny flap is shut (push on the small silver rectangle on the front of the camera and make sure it's attached firmly)

- make sure that the camera cable, or FFC (flexible flat cable) is fully inserted into the camera and the Raspberry Pi.

- On the Raspberry Pi, make sure the blue side of the FFC is facing towards the USB ports

- On the camera, make sure the blue side of the FFC is facing up

- Make sure that there are no holes or rips in the FFC. This is a common issue: a crash could have caused a tear, or a hole could have been made when soldering. If this is the case, you will need a new FFC

- rerun the vision script
```

```{trouble}
The rosbridge node is not running-

---
The last line printed out should include the phrase `Rosbridge websocket server started on port 9090`

If not:

- make sure you have no other programs using the same port as the Rosbridge server (9090)

try rerunning the script.
```

```{trouble}
The web interface does not say `connected` at the top.

---

- try using Google Chrome to open the web interface

wait another 10 seconds and try refreshing again.
```

```{trouble}
When I move the drone up and down the height reading graph does not change.

---

Recheck the ToF node. Rerun the node if needed and then refresh the browser.
```


```{trouble}
There is no data on the `x` and `y` velocity graphs or they do not change when moving the drone

---
Check that the vision node in Screen is running. Rerun the node if needed and refresh the browser.
```

```{trouble}
There is a long delay between when you move the drone and when the graphs change.

---

If you are running the drone in managed mode, this is probably due to latency in your home network. Take some of the devices offline, or restart the drone and fly in AP mode.
```

```{trouble}
The motors on the drone do not spin when armed on the web interface 

---

Plug the USB into a computer with Cleanflight Configurator and verify the following settings in Cleanflight:

- the yaw is flipped 180 degrees in the `"Configuration"` tab

- the receiver is set to `MSP RX Input` (so that the FC can receive commands from the Raspberry Pi over USB) in the `"Configuration"` tab

- the ESC/Motor protocol is set to PWM in the `"Configuration"` tab.
```

```{trouble}
The drone does not get off the ground when commanded to takeoff.

---

- make sure that the arrows inscribed on the propellers are visible from the top of the drone

- make sure that the arrows on the props are in the correct direction

- Take off the propellers from your motors and plug the battery into your drone. In Cleanflight Configurator, navigate to the motors tab, click `"I agree to the risks"`, and try to spin up each motor. Make sure that each motor spins in the correct direction.

- Make sure that when you spin up motor 1, the correct motor spins (the bottom right). Do this for all of the motors.
```