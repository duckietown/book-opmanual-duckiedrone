# Nodes

This section elaborates on all of the ROS nodes that run on your drone to make it fly autonomously. These are described in the order in which they appear in `pi.screenrc`: the pattern \`# in the headers serves to remind that in screen you can move between the various nodes by typing \`# where # is the node number.

## \`0: roscore
Starts up a ROS master to allow the nodes to find each other.

* Runs: `roscore`

## \`1: FC
The flight controller node controls what mode the drone should be in based on the user input and on safety checks. For example, if any of the heartbeats stop publishing, the mode controller disarms the drone. If the mode is "ARMED" or "DISARMED", the flight controller node sends static command values, but if the mode is "FLYING", then the node sends the fly_commands topic to the flight controller board.

Flight Controller interfaces with the flight controller board to extract the IMU and battery data, and to publish the roll, pitch, yaw, and throttle commands which are used to control the attitude of the drone. 

You will need to start this node explicitly (press enter on screen 1) as a safety measure to prevent the drone from flying until you are really ready.

* Python script: 
    * `flight_controller_node.py`
* Hardware interfacing: 
    * flight controller board
* Publishers:
    * `/pidrone/imu`
    * `/pidrone/battery`
    * `/pidrone/mode`
* Subscribers:
    * `/pidrone/fly_commands`
    * `/pidrone/desired/mode`
    * `/pidrone/heartbeat/range`
    * `/pidrone/heartbeat/web_interface`
    * `/pidrone/heartbeat/pid_controller`
    * `/pidrone/state`

## \`2: PID
The PID controller node controls the flight of the drone by running a PID controller on the error calculated by the desired and current velocity and position of the drone.

Most of the PID loop tuning values, and the implementation of a PID control loop is actually in `scripts/pid_class.py`.

* The 5 columns of numbers that are printed on this screen actually come from pid_class.py, and represent the following:
    * throttle command for flight controller (1200=least lift)
    * target height minus actual height (millimeters)
    * component of throttle command caused by Proportional component of PID
    * component of throttle command caused by Integral component of PID
    * component of throttle command caused by Derivative component of PID


* Python script: 
    * `pid_controller.py`
* Hardware interfacing: 
    * None
* Publishers:
    * `/pidrone/fly_commands`
    * `/pidrone/position_control`
    * `/pidrone/heartbeat/pid_controller`
* Subscribers:
    * `/pidrone/state`
    * `/pidrone/desired/pose`
    * `/pidrone/desired/twist`
    * `/pidrone/mode`
    * `/pidrone/desired/mode`
    * `/pidrone/position_control`
    * `/pidrone/reset_transform`
    * `/pidrone/picamera/lost`

## \`3: SE
The State Estimator node unifies the different state estimators so that the user only has to call this script to interact with state estimators. This node publishes to `/pidrone/state`, which offers the best state estimate based on whichever state estimators are to be used, depending on the command-line arguments that the user passes into this script. 

The different state estimators (in `scripts/StateEstimators/`) are:
- ema: uses an exponential moving average
- ukf2d: UKF with a 2D state vector
- ukf7d: UKF with a 7D state vector
- ukf12d: UKF with a 12D state vector

The state typically consists of the x,y,z positions and velocities, and the yaw of the drone. We've implemented several state estimators that vary in complexity. You will be implementing a state estimator that uses an Unscented Kalman Filter (UKF) in a future project.

* Python script: 
    * `state_estimator.py`
* Hardware interfacing: 
    * None
* Publishers:
    * `/pidrone/state`
* Subscribers (one of):
    * `/pidrone/state/ema`
    * `/pidrone/state/ukf_2d`
    * `/pidrone/state/ukf_7d`
    * `/pidrone/state/ukf_12d`


## \`4: Vision

* Runs: 
    * raspicam_node (from [github.com/UbiquityRobotics/raspicam_node](https://www.github.com/UbiquityRobotics/raspicam_node))
* Hardware interfacing: 
    * Raspberry Pi camera
* Publishers:
    * `/raspicam_node/motion_vectors`

## \`5: Optical Flow
The Optical Flow node subscribes to the optical flow motion vectors published by the vision node and publishes linear velocity calculated from that.

* Python script: 
    * `optical_flow_node.py`
* Hardware interfacing: 
    * None
* Publishers:
    * `/pidrone/picamera/twist`
* Subscribers:
    * `/raspicam_node/motion_vectors`
    * `/pidrone/range`

## \`6: Rigid Transform
This node uses OpenCV to calculate the change in position of the drone using the camera.

* Python script: 
    * `rigid_transform_node.py`
* Hardware interfacing: 
    * None
* Publishers:
    * `/pidrone/picamera/pose`
    * `/pidrone/picamera/lost`
* Subscribers:
    * `/pidrone/reset_transform`
    * `/pidrone/position_control`
    * `/pidrone/state`
    * `/raspicam_node/image/compressed`
    * `/pidrone/range`

## \`7: TOF
The TOF node communicates with the VL53L0X Time Of Flight distance sensor using I2C and publishes the sensor's range readings.

* Python script: 
    * `tof_node.py`
* Hardware interfacing: 
    * Time Of Flight sensor
* Publishers:
    * `/pidrone/range`

## \`8: rosbridge
This node allows the web dashboard to communicate with ROS nodes on the drone.

* Publishers:
    * `/pidrone/desired/mode`
    * `/pidrone/heartbeat/web_interface`
    * `/pidrone/position_control`
    * `/pidrone/desired/twist`
    * `/pidrone/desired/pose`
    * `/pidrone/reset_transform`
    * `/pidrone/map`

## \`9: web_vid_serv
This node allows the web dashboard to request a camera stream of the drone. This node doesn't run by default but if you want to see what the drone's camera is seeing and if you have the processing power to spare on the drone you can press enter on this screen.

## \`10 free1
This screen is an unused console that you can use to run any additional commands you need to. One way to get to this screen is to type \`9 then \`n

## \`11 free2
This screen is an another unused console that you can use to run any additional commands you need to. One way to get to this screen is to type \`9  \`n \`n


