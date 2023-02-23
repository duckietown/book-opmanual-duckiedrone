# Flying Your Drone {#flight status=ready}

In order to fly, you will need:

* Fully assembled drone
* Charged battery
* Base station
* Safety goggles
* Highly textured planar surface, such a poster board with scribbles. This should have considerable and distinct markings for the camera to process. Alternatively, a patterned carpet will work.


<figure>  
   <figcaption>Example of a highly textured planar surface.</figcaption>
   <img style='width:200px' src="photos/htps.png"/>
</figure>


## Environment Checks {#checks-environment}

- You are in an open space that is free of obstructions

- You've alerted those around you that you are going to fly and have told them to clear the area

- You are wearing safety goggles

- The surface you are flying over is not reflective, and is not uniform in details. Ideally, you've created a highly textured planar surface, which is a poster board with a bunch of scribbles and shapes. A patterned carped will work fine as well.

<figure>
    <figcaption>Example of a highly textured planar surface.</figcaption>
    <img style='width:15em' src="photos/htps.png"/>
</figure>  

## Hardware Checks {#checks-hardware}

If not already, disconnect the battery before performing the following safety checks.

### Wire Management

Spin the props with your finger and make sure there are no wires in the way. If wires do get close, use a zip tie to hold the wires to the frame, away from the props.

### USB Connection

Make sure that the flight controller USB is plugged into the Pi. Any of the USB ports will work.

## Software and Sensors Checks {#checks-software}

### Power

Plug the battery into your drone.

### Connection

Connect to your drone's wifi network. By default, the wifi is called *defaultdrone* and the password is *bigbubba*

### Code Editor

In a new tab, browse to your drone's code editor: [192.168.42.1:8081](http://192.168.42.1:8081).

This is not installed in the 2022 version of the drone, so instead use
SSH.  Navigate to the `pidrone_pkg` directory and run `screen -c
pi.screenrc` to start the Screen session.  Screen is a program that
allows you to run multiple terminals in one ssh session.  The screen
will persist even if the ssh session is disconnected and you log in
again.  However it will disappear if you reboot the drone.  Run
`screen -x` to see what screen sessions are running and reconnect to a
session that you have disconnected from.  Be careful to only have one
screen session running at a time.

The screen session will start the ROS nodes needed to run your drone
and make it fly.  However it will not start the flight controller
node; we ask you to start this node manually because you should only
run it if you are prepared for your propellers to spin.  The screen
'escape' key is back-tick.  The "tick" \` key is typically located to
the left of the `1` key, and is on the same key as the tilde `~`. Note
that you will not see anything appear when you are typing \` `1`

To navigate the screen tabs, use the following commands:
\`1, `2, etc to navigate to a particular window. 

\`" : Open tab menu

\`n : Go to next tab

\`p : Go to previous tab

\`' : Ability to enter full numbers so can enter stuff like 10 and 11

### Start the Flight Code

1. If there is not a terminal open at the bottom of the code editor, then open a new terminal: Menu (three horizontal lines in the top left) > Terminal > New Terminal

1. In the terminal, type type `roscd pidrone_pkg` and press enter.

1. Calibrate the accelerometer by typing  `python scripts/calibrateAcc.py` and press enter.

1. Start up the flight code by typing the command `./start` and press enter.

### Start the Flight Controller Node in Sensors-only Mode

1. In the terminal, navigate to the flight controller node by typing "tick 1": \` `1` . 

1. Press enter to start the python script

1. When prompted, "Are you ready to fly?" type `n` and press enter to run in sensors-only mode. This allows us to use the flight controller sensors without the chance of the motors spinning while we are testing the ir and camera sensor in the next steps.

### Web Interface

1. In a new tab, browse to your drone's web interface: [http://192.168.42.1](http://192.168.42.1)

1. Press connect on the web interface to connect to your drone. If the web interface does not say "connected", then wait about 5 seconds and refresh the page

### Check the IR Sensor

While looking at the Height Chart in the web interface, move the drone up and down and make sure you see changes in the IR graph on the web interface

### Check the Camera

While looking at the X Velocity Chart in the web interface, move the drone to the left and right and verify that the graph changes. While looking at the Y Velocity Chart in the web interface, move the drone forward and back and make sure the graph changes.

### Check the ROS Nodes

In the terminal of the code editor, go through each of the screens using \` n, where n is a number 1-5, and make sure there are no errors printed out. It is normal that there may be an error at the top of each screen that says something about not connecting to ROS master, but that is OK because it takes a bit for ROS to startup. Each screen should say "started" or "publishing".

1. tick 1 is the flight controller node; you've already seen this one

2. tick 2 is the pid controller; this sends the roll, pitch, yaw, and throttle commands to the flight controller

3. tick 3 is the state estimator; this combines sensor data to estimate the state (position, velocity, orientation) of the drone

4. tick 4 is the camera node; this gets velocity and position data from the camera

5. tick 5 is the infrared node; this gets height readings from the IR sensor


## Fly

### Familiarize yourself with the keyboard commands

Find and read the keyboard commands to control the drone at the
bottom of the web interface. The keyboard focus must be on the web page for these commands to work: you may need to click on the screen before typing the first keyboard command.

The primary keys you'll need are the spacebar (to disarm the drone), the semicolon `;` (to arm the drone), and `t` (to takeoff). The most important key is the spacebar.

**If anything goes wrong be prepared to immediately hit spacebar to disarm the drone.**

Other useful keys are `i` `j` `k` and `l` which allow you to fly the drone around. The drone will attempt to hover in one place, but if it moves too much to one side, you can steer it back to the center using these keys.

### Orient the drone

Rotate the drone so that the camera end is facing towards you and the flight controller is facing away from you.  In this way the keyboard controls (I,j,k,l) will match the drone's orientation. ***I - foward*** (flight controller side), ***J - left***, ***K - backward*** (camera side), ***L - right***

### Restart the Flight Controller Node for Flight

1. In the terminal in the code editor, navigate back to the flight controller node using tick 1.

1. Quit the flight controller node by  typing control-c (hold down the *ctrl* key and press the *c* key)

1. Rerun the flight controller script by pressing the up arrow on your keyboard (this brings back the last script that was run) and then press enter

1. When prompted, "Are you ready to Fly?" type `y` and press enter to start the flight controller node

### Takeoff sequence

1.  First arm your drone by pressing `;`.  The propellers should start
spinning slowly. If they spin fast, or you hear strange noises,
immediately disarm the drone.  If they still
do not spin, check the flight_controller_node. This is where any error message will be printed out.

1. Disarm your drone (spacebar) and ensure that the propellers slow down almost immediately and then stop spinning. If there is a delay, then there is likely network latency and this could cause flight issues. If you are connected to the drones network and there is delay, try restarting the Pi. If you are connected to your home network and there is delay, restart the Pi and use the drone's network to fly instead.

1. Try arming (`;`) and disarming (spacebar) again to ensure that the drone is responsive.

1.  If all goes well, arm the drone again, then press `t` to takeoff.  Be prepared to disarm the
drone if anything goes wrong.

1.  Move in the plane using `i`, `j`, `k`, `l` on the keyboard.  When
not moving the drone will try to maintain zero planar velocity but may
drift.

** Congrats on flying! **


## Flying Modes

There are two modes of flight for the drone, velocity control and position control. In velocity control, the drone tries to maintain zero velocity in the x and y directions; however, the drone can drift over time using just a control loop on the velocity. In position control, the drone is able to prevent itself from drifting. Information on each mode is included below. [This video](https://www.youtube.com/watch?v=WTohnsKs7dU) shows
velocity mode, where it drifts, followed by position mode, followed by
velocity mode again.

### Velocity Control

The default mode when starting is velocity mode, where the keyboard
commands control planar velocity.  When no keys are pressed the
drone's velocity setpoint is zero, so it tries to maintain still.  It
estimates its velocity using the optical flow computed from the camera
frames. This estimate only works over a textured surface; when flying
over a non-textured surface it will cause the drone to inaccurately
estimate its velocity and fly out of control.  A repeating texture is
fine, as long as it has texture (e.g., a carpet with a pattern).
Using just the velocity, the drone will tend to drift
over time. The key `v` activates velocity mode, and the
drone is always in this mode on when it starts flying.


### Position Control

Because velocity mode can drift, we have implemented a position hold
mode, where the drone computes its offset relative to automatically
detected features from the downward pointing camera.  This mode must
be activated over a planar surface with a non-repeating texture, such
as a poster board with scribbles in different colors and shapes.  When
position mode is activated, it takes a picture of the first frame, and
then continuously estimates its offset from this frame.  If it sees
features in the first frame, it computes its position relative to the first image;
otherwise it computes its position relative to the previous image it saw, and adds
the change in position to its current position.

Type `p` to active position hold, and `r` to reset the first frame
where offsets are computed.  A well-tuned drone can hold the same
position indefinitely on power, and for almost the entire battery
when on battery.  (At the end of the battery it will oscillate more
and lose its position.)

When in position mode, the keyboard commands tell the drone to
maintain a setpoint that is a defined offset from the origin, defined
by the saved first frame.  That is, if you fly left, it will try to
hold its position a defined offset to the left of the first frame.  Of
course if the drone gets too far from the first frame, it can no
longer compute a global estimate and will drift away.  To rectify this
problem, you need to compute a global map and localize in that map, as
described in the next section.

Note: If the drone drifts too far without being able to make a position estimate, the drone automatically switches back to velocity control. This is a safety feature and the threshold can be adjusted in the `pidrone_pkg/params/thresholds.yaml` file.
