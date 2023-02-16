(overview_tof_sensor)=
# Overview

## Preface

At a high level, a **sensor** is a device that _observes_ something about the world and reports its observations on an electrical wire. For example, a camera can be a sensor.

In contrast, an **actuator** is a device that _does_ something when provided power via an electrical wire. For example, a motor can be an actuator.

The simplest possible robot is one that has only actuators. However, a robot with any amount of autonomy would also require sensors. This is because such a robot would need observations about its world in order to decide what to do with its actuators.

In this part of the build, you will be adding your first sensor to the drone: the time of flight (TOF) sensor. The TOF sensor is used to measure distance. We’ll provide more details about the hardware used in this portion of the build, and then get into the instructions.

```{attention} You will need Build Part 1 completed before you can begin this build part.
```
## Required Materials
```{list-table} Materials
:header-rows: 1
:name: materials-tof-sensor

* - Part
  - Quantity
* - TOF Sensor & wire
  - 1
* - Soldering tools
  - 1
```

## TOF Sensor
The TOF (**Li**ght **d**etection **a**nd **r**anging - **Lidar**) sensor is used to measure distance. On the drone, we use this sensor to measure the height of the drone above the ground. Lidar enables autonomous vehicles to “see” by generating and measuring millions of data points in real time, creating a precise map of its ever-changing surroundings for safe navigation.

```{image} ../_images/components-official/TOF-sensor.jpg
:width: 200px
:align: center
```

## Build progress
After completing this section, you will have the Pi Hat connected to the Raspberry Pi, and the Hat will have soldered on:

* A 2-pins connector to connect the UBEC
* A 2-pins connector to select the WiFi mode of the Raspberry
* The TOF cable

See the [following figure](pi_hat_progress):

```{figure} ../_images/tof-sensor/pi_hat_progress.jpg
:width: 300px
:name: pi_hat_progress

Pi Hat progress
```
The TOF sensor receives power from the Pi Hat, and the sensor output signal is received by the Pi, using the SCL and SDA inputs (the sensor uses a protocol called I2C).
