# Nodes

This section elaborates on all of the ROS nodes that run on your drone to make it fly autonomously. These are described in the order in which they appear in pi.screenrc.

## \`0: rcore
Starts up a ROS master to allow the nodes to find each other.

* Runs: `roscore`

## \`1: FC
The flight controller node controls what mode the drone should be in based on the user input and on safety checks. For example, if any of the heartbeats stop publishing, the mode controller disarms the drone. If the mode is "ARMED" or "DISARMED", the flight controller node sends static command values, but if the mode is "FLYING", then the node sends the fly_commands topic to the flight controller board.

Flight Controller interfaces with the flight controller board to extract the IMU and battery data, and to publish the roll, pitch, yaw, and throttle commands which are used to control the attitude of the drone. 

You will need to start this node explicitly (press enter on screen 1) as a safety measure to prevent the drone from flying until you are really ready.

* Python script: flight_controller_node.py
* Hardware interfacing: flight controller board
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

Most of the PID loop tuning values, and the implementation of a PID control loop is actually in scripts/pid_class.py.

The 5 columns of numbers that are printed on this screen actually come from pid_class.py, and represent the following:
    * throttle command for flight controller (1200=least lift)
    * target height minus actual height (millimeters)
    * component of throttle command caused by Proportional component of PID
    * component of throttle command caused by Integral component of PID
    * component of throttle command caused by Derivative component of PID

* Python script: pid_controller.py
* Hardware interfacing: None
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
The State Estimator node unifies the different state estimators so that the user only has to call this script to interact with state estimators. This node publishes to /pidrone/state, which offers the best state estimate based on whichever state estimators are to be used, depending on the command-line arguments that the user passes into this script.
    The different state estimators (in scripts/StateEstimators/) are:
        - ema: uses an exponential moving average
        - ukf2d: UKF with a 2D state vector
        - ukf7d: UKF with a 7D state vector
        - ukf12d: UKF with a 12D state vector
 The state typically consists of the x,y,z positions and velocities, and the yaw of the drone. We've implemented several state estimators that vary in complexity. You will be implementing a state estimator that uses an Unscented Kalman Filter (UKF) in a future project.

* Python script: state_estimator.py
* Hardware interfacing: None
* Publishers:
    * `/pidrone/state`
* Subscribers (one of):
    * `/pidrone/state/ema`
    * `/pidrone/state/ukf_2d`
    * `/pidrone/state/ukf_7d`
    * `/pidrone/state/ukf_12d`


## \`4: Vision

* Runs: raspicam_node (not in pidrone_pkg. from [github.com/UbiquityRobotics/raspicam_node](https://www.github.com/UbiquityRobotics/raspicam_node))
* Hardware interfacing: Pi camera
* Publishers:
    * `/raspicam_node/motion_vectors`

# TODO:
## CONTINUE WORK HERE

## \`5: Optical Flow
xState Controller subscribes to all of the sensor data and uses a filter to exstimate the state of the drone. The state typically consists of the x,y,z posxitions and velocities, and the yaw of the drone. We've implemented several statex estimators that vary in complexity. You will be implementing a state estimatxor that uses an Unscented Kalman Filter (UKF) in a future project.

x* Python script: state_estimator.py
* Hardware interfacing: None
*x Publishers:
  x  * "/pidrone/state"
* Sxubscribers:
    x* "/pidrone/picamera/twist"
    *x "/pidrone/picamera/pose"
    * x"/pidrone/infrared"
    * "x/pidrone/imu"
    * "/xpidrone/reset_transform"

## \`6: Vision
The vision node interfaces with the picamera to provide velocity and position estimates. There are several vision files used to do this. `vision_flow_and_phase.py` uses the python scripts `analyze_flow.py` and `analyze_phase.py` to estimate the velocity and position of the drone using optical flow vectors and rigid transformations, respectively. These values are published for use by the state_estimator. Another vision node is `vision_localization_offboard.py`, which uses localization to provide the position of the drone to the state estimator. Others exist as well, and you will be writing vision nodes in future projects.

* Python script: vision_flow_and_phase.py
* Hardware interfacing: Pi camera
* Publishers:
    * "/pidrone/picamera/twist"
    * "/pidrone/picamera/pose"
* Subscribers:
    * "/pidrone/state"

## \`7: Infrared
Infrared is used to interface with the analog to digital converter (ADC) which is connected to the infrared sensor. This node is used to convert the data from the ADC into usable range readings to publish for use by the state estimator.

* Python script: infrared_pub.py
* Hardware interfacing: Infrared sensor
* Publishers:
    * "/pidrone/infrared"
