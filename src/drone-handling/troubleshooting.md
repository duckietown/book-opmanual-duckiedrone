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

```{trouble}

My Raspberry Pi does not boot or the motors do not turn on.
---

You should verify that each part of the drone is receiving power.  The
Raspberry Pi indicates it has power with a red power LED.  The motors indicate
they are receiving power by beeping once.  You can also check each
part with the multimeter.  Verify that there is a 12 Volt connection
between power and ground on the power distribution board.  And verify
that the Pi is receiving 5 volts from the BEC.  

## Pi Issues

Most of the next debugging steps require getting "into" your Pi.  So
if your PI doesn't boot and display an access point, you are stuck.
If your Pi is not powering on, verify with a multimeter that the Pi
pins are receiving the right voltage on input.  You can find a mapping
of the GPIO pins
[here](https://www.raspberrypi.org/documentation/usage/gpio/).  Verify
that each power pin is receiving 5 volts compared to each ground pin
with the multimeter.

If your Pi is receiving 5 volts on its power/ground pins, but no red
light turns on, then it might have gotten fried.  This can happen if
you wire or short the power/ground pins on the Pi, so try replacing
the Raspberry Pi.

If it is receiving power and turning the red light on, then something
might be wrong with your SD card. Verify that your SD card has the
correct image flashed on it, and that it is seated in the Pi so that
it can boot. If all this doesn't work, then find a keyboard and
monitor to plug the Pi into during boot, to see what is going on
during the boot process.  There may be an error message being printed
on the screen that will give more information.

## Camera

Now verify that the camera is working.  If the camera node is not
starting in screen, use `raspistill` to verify that it is plugged in.
You can try `raspi-config` and make sure it is enabled.  Also it is
very common for the camera cable to be plugged in backwards, or
plugged into the wrong slot on the Pi.  (There are two possible slots
that fit the cable.)  Make sure it is plugged into the slot marked
"camera", and that the cable is facing the right way. (The metal parts
of the cable should be facing the pins in the slot.)  And make sure it
is seated all the way.

If none of these things make "raspistill" work, try plugging your Pi
into someone else's camera, and someone else's Pi into your camera,
and try all of the above debugging steps.  You can also consider if
the cable is bad.  For example if you bend the cable too much, it will
fatigue and then break the wires; or if a prop strikes the cable, it
might cause the cable to break.

If your Pi and cable works with someone else's camera but not yours,
try replacing the camera.  If your camera and cable work with someone
else's Pi but not yours, try replacing the Pi.

## Range Sensor

The range sensor passes information through the Adafruit board.  Use
the multimeter to verify the three wires going to the range sensor
have sensible values.  Check power to ground first; then check the
signal wire to ground.  You should see the signal voltage change in
the multimeter based on the range reading (moving your hand closer and
farther from the sensor.)

If that is working, then check the Adafruit board.  Verify that you
can read the analog range voltage reading on the appropriate pin on
that board.  Then verify that it is getting power.

If all that looks good, then check the connection to the Adafruit
board and the Raspberry pi.  Make sure the Pi GPIO pin is accurately
reading the adafruit output value.

## Flight Controller

Finally check the flight controller.  When the flight controller
connects to the motors, it will make a "low beep, high beep" sound.
So verify you hear the "do do do" from the motors, indicating they
have power, and then the "low, high" indicating the flight controller
can talk to them. If that doesn't work, check the connection between
the flight controller, ESCs, and motors.

Inside the Pi, make sure you can calibrate the accellerometer, and run
the flight controller node.  If those don't work, go back and recheck
your Cleanflight configuration.

Sometimes the flight controller gets wedged into a state where you
can't talk to it in Cleanflight.  You can get it unwedged by shorting
two pins on the board and following the instructions in Cleanflight.
Once you do this though, you'll need to set the Cleanflight
configuration again.

## Flight Issues

Before each flight, physically inspect the drone.  Make sure that your
camera is mounted firmly, pointed downwards.  Make sure the range
sensor is pointed downwards and hasn't gotten rotated.  Make sure the
flight controller board is level and firmly attached, or the IMU and
gyroscope will return incorrect readings.  Any of these issues could
cause poor flight behavior.  Also make sure each propellor is
tightened down all the way.

If your drone flips the first time you try to take off, the motors are
spinning the wrong way, or the props are on upside-down.  If your
drone makes funny noises when arming, either the props are not
tightened all the way, or they are stricking a wire.  Tape everything
down as much as possible.

If the drone is not stable during flight, you should make sure that
the props are all tightened down.  Make sure the ESCs have been
calibrated following as in (this
video)[https://www.youtube.com/watch?v=csCBMF8P3qg].

After doing all these steps, you can try to tune the PID gains as
described in our PID project.

A well-tuned drone can hover with velocity zero with some drifting,
but not tons of drifiting.  It should be able to hover with position
hold indefinintely.

