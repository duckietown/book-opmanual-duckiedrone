(build_troubleshooting)=

# Troubleshooting
It is very very common for something to go wrong during your build.
Count on it.  The goal is to systematically figure out what is wrong
and fix it.  Mastering this process is essential to any robot project,
because things will always go wrong.

The high-level bit when troubleshooting is to try to isolate the
problem systematically.  Rather than simply redoing part of the build
or replacing a part, try to systematically verify what parts are
working and what parts are not working.  Your drone will not fly until
everything works!

## Power issues

```{trouble}

My Raspberry Pi does not boot.
---

You should verify that each part of the drone is receiving power.  The
Raspberry Pi indicates it has power with a *red* power LED.

If your Raspberry Pi is not powering on, verify with a multimeter that the Raspberry Pi
pins are receiving the right voltage on input.  You can find a mapping
of the GPIO pins [here](https://www.raspberrypi.org/documentation/usage/gpio/).
Verify that each power pin is receiving 5 Volts compared to each ground pin with the multimeter.

Make sure you did not use metal screws to mount the camera to the frame as they can cause a short.
 
If your Raspberry Pi is receiving 5 volts on its power/ground pins, but no red
light turns on, then it might have gotten fried.  This can happen if
you wire or short the power/ground pins on it, so try replacing
the Raspberry Pi.
```

```{trouble}
The motors do not turn on.
---
The motors indicate they are receiving power by beeping once. You can also check each
part with the multimeter.  Verify that there is a 12 Volt connection
between power and ground on the power distribution board.  And verify
that the Raspberry Pi is receiving 5 volts from the UBEC.  
```

## Raspberry Pi Issues

Most of the next debugging steps require getting "into" your Raspberry Pi using ssh,
 check the [](./first-connection.md) chapter if you are not connected.

```{trouble}
My Raspberry Pi is receiving power and turning the red light on, but it doesn't boot.

---
Something might be wrong with your SD card.

*   Verify that your SD card has the correct image flashed on it.

*   Check that the SD card is inserted in the Raspberry Pi so that it can boot.

If all this does not work, find a keyboard and
monitor to plug the Raspberry Pi into during boot, to see what is going on
during the boot process.

There may be an error message being printed on the screen that will give more information.
```
## Camera
Now verify that the camera is working. 

```{trouble}
I'm in the Screen session, but the camera node is not
starting.

---

Use `raspistill` to verify that it is plugged in.

You can try `raspi-config` and make sure it is enabled.
Also it is very common for the camera cable to be plugged in backwards, or
plugged into the wrong slot on the Raspberry Pi.  (There are two possible slots
that fit the cable.)  Make sure it is plugged into the slot marked
`"camera"`, and that the cable is facing the right way. (The metal pins
of the cable should be facing the pins in the slot.)  Make sure it
is seated all the way.

If none of these things make `raspistill` work, try plugging into your Raspberry Pi 
someone else's camera, and someone else's Raspberry Pi into your camera,
and try all of the above debugging steps.  You can also check if
the cable is bad.  For example if you bend the cable too much, it will
fatigue and then break the wires; or if a prop strikes the cable, it
might cause the cable to break.

If your Raspberry Pi and cable work with someone else's camera but not yours,
try replacing the camera.  If your camera and cable work with someone
else's Raspberry Pi but not yours, try replacing the Raspberry Pi.
```
## Flight Controller

Finally check the Flight Controller.  When the Flight Controller
connects to the motors, it will make a "low beep, high beep" sound.
So verify you hear the "do do do" from the motors, indicating they
have power, and then the "low, high" indicating the Flight Controller
can talk to them. If that doesn't work, check the connection between
the Flight Controller, ESCs, and motors.

Inside the Raspberry Pi, make sure you can calibrate the accelerometer, and run
the Flight Controller node.  If those don't work, go back and recheck
your Cleanflight configuration.

## Flight Issues

Before each flight, physically inspect the drone.

Make sure that:

* your camera is mounted firmly, pointed downwards.
* the range sensor is pointed downwards and hasn't gotten rotated.
* the Flight Controller board is level and firmly attached, or the IMU and gyroscope will return incorrect readings.
* each propeller is tightened down all the way.

Any of these issues could cause poor flight behavior.

If your drone flips the first time you try to take off, the motors are
spinning the wrong way, or the props are on upside-down.  If your
drone makes funny noises when arming, either the props are not
tightened all the way, or they are striking a wire.  Tape everything
down as much as possible.

If the drone is not stable during flight, you should make sure that
the props are all tightened down.  Make sure the ESCs have been
calibrated following as in [](esc_calibration).

A well-tuned drone can hover with velocity zero with some drifting,
but not too much.  It should be able to hover with position
hold indefinintely.

