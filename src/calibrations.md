# Accelerometer calibrations

The IMU is embedded in the flight controller and includes a gyroscope and an accelerometer, which respectively produce angular rate (in degrees/second) and linear acceleration measurements (normalized to gravitational acceleration at sea level `g` = 9.81 m/s^2).

![](https://ethidsc.atlassian.net/wiki/download/attachments/2247065601/image-20220812-103725.png?api=v2)

Calibrating the accelerometer provides the “zero” plane around which the FC will stabilize the drone during flight, and is a procedure that should be repeated before each flight.

## Method 1: calibration through CleanFlight

1.  Connect to the FC ([https://ethidsc.atlassian.net/wiki/spaces/DTSKY/pages/2233466906/6.1+Setting+up+the+Flight+Controller#Connecting-to-the-Flight-Controller-(FC)%5BhardBreak%5D](https://ethidsc.atlassian.net/wiki/spaces/DTSKY/pages/2233466906/6.1+Setting+up+the+Flight+Controller#Connecting-to-the-Flight-Controller-(FC)%5BhardBreak%5D))
    
2.  Navigate to the “Setup” page
    
3.  Place the drone on a (very) flat surface
    
    1.  Make sure the drone is level on the flat surface
        
4.  Click on “Calibrate Accelerometer”
    
    1.  Do not move the drone while the calibration is in progress or it will invalidate the calibration
        
5.  Wait for a few seconds. A successful outcome will produce a “reset” of pitch and roll measurements and the rendering of the drone’s attitude will show a level condition. Moreover, a message will appear on the top left of the CleanFlight interface saying “Accelerometer calibration finished”
    

![](https://ethidsc.atlassian.net/wiki/download/attachments/2247065601/Drone-IMU-calibration.gif?api=v2)![](https://ethidsc.atlassian.net/wiki/download/attachments/2247065601/image-20220812-104859.png?api=v2)

## Method 2: calibration through the Dashboard

  
The same result as above can be obtained by connecting to the Dashboard instead of directly hard-wiring the FC to the base station.  

1.  Connect to the Dashboard ([https://ethidsc.atlassian.net/l/cp/uL6aFTX5](https://ethidsc.atlassian.net/l/cp/uL6aFTX5))
    
2.  Navigate to the Robot > Mission Control page
    
3.  Find the “IMU - Orientation” mission control block
    
4.  On the top right corner of this block, find and click on the “Calibrate IMU”
    
    1.  the data streaming will freeze for a few seconds while the calibration is undergoing, and it will resume once the calibration is complete.
        

![](https://ethidsc.atlassian.net/wiki/download/attachments/2247065601/Screen%20Recording%202022-08-12%20at%2013.11.27.gif?api=v2)

## Resetting Yaw offset
The IMU calibration "resets" roll and pitch values to zero, but not the yaw.

```{note}
This part is optional and not strictly needed to have stable flight.
```

Zeroing the yaw defines the new “forward” direction of the drone, and it can be done through the CleanFlight interface.

1.  Connect the FC
    
2.  Navigate to the “Setup” page
    
3.  Click on “Reset Z axis, offset”
    
4.  A successful outcome will (1) show a new offset value on the reset button itself, and (2) the rendering will show the drone oriented towards the new zero.
    

![](https://ethidsc.atlassian.net/wiki/download/attachments/2247065608/Screen%20Recording%202022-08-12%20at%2014.19.19.gif?api=v2)